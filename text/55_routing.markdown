## Routing

### <a id="patch-verb"></a>PATCH Verb

Rails 4 introduces support for the HTTP PATCH verb. According to [RFC
5789](http://tools.ietf.org/html/rfc5789), the PATCH verb is more appropriate
for applying "partial modifications to a resource."

Traditionally, Rails has used the PUT verb for updates of RESTful resources.
However, the RFC states that PUT should be used only to "overwrite a resource
with a complete new body," and *not* for simply updating parts of it.

All that to say that Rails conventions have been using PUT incorrectly.

Rails 4 retains support for update requests coming in via the PUT verb, yet
adds support for those same types of requests coming in via the PATCH verb too.

Consider a typical RESTful controller with an `update` action:

@@@ ruby
# app/controllers/widgets_controller.rb
class WidgetsController < ApplicationController
  # ...

  def update
    @widget = Widget.find(params[:id])
    @widget.update_attributes(params[:widget])

    redirect_to @widget
  end
end
@@@

In Rails 4, requests for `PUT /widgets/1` and `PATCH /widgets/1` will both
route to the `WidgetsController#update` action.

At a minimum, you only need to be aware of the PATCH verb; the addition should
not cause any upgrade pains as PUT requests continue operating as they always
have.

That said, it is recommended that you consider transitioning to using PATCH
instead of PUT when using your Rails application as an HTTP/RESTful API.

### <a id="routing-concerns"></a>Routing Concerns

This section coming soon.