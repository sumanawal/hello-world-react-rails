# Building Hello World using react-rails gem

- Add `gem 'react-rails'` in Gemfile
- Execute `bundle install`
- Execute `rake webpacker:install`
- Execute `rake webpacker:install:react`
- Execute `rails g react:install`
- Generate a <b>HelloWorld</b> react component

  - `rails g react:component HelloWorld greeting:string` This will generate `app/javascript/components/HelloWorld.js` with following content.
  ```
    import React from "react"
    import PropTypes from "prop-types"
    class HelloWorld extends React.Component {
      render () {
        return (
          <React.Fragment>
            Greeting: {this.props.greeting}
          </React.Fragment>
        );
      }
    }

    HelloWorld.propTypes = {
      greeting: PropTypes.string
    };
    export default HelloWorld

  ```

Follow following to create controller, view and render react component.
```
  # Create app/controllers/hello_world_controller.rb
  class HelloWorldController < ApplicationController
    def index
      @greetings = "Hello this is from rails controller"
    end
  end

  # Create app/views/hello_world/index.html.erb
  <%= react_component("HelloWorld", { greeting: @greetings }) %>

  # In routes.rb add following
  root 'hello_world#index'
```

- Start the server and visit root page `localhost:3000` and enjoy.
