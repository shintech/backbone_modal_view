## Backbone Modal View

### Synopsis

Bootstrap Modal in a Backbone Marionette View

### Usage

#### TableView.js

    import ModelModalView from 'backbone_modal_view'
    
    const modelModalView = new ModelModalView()

    const TableView = Backbone.Marionette.View.extend({
      
      events: {
        'click .table-row': 'handleClick'
      },
    
      initialize: function () {
        modelModalView.template = require('./modal-view-template.html')
      },
    
      handleClick: function (e) {
        const id = $(e.currentTarget).data('id')
        const model = this.collection.get(id)
        
        modelModalView.model = model
        modelModalView.render()
      }
    })

    export default TableView

#### modal-view-template.html

    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h3 class="modal-title"><%= name %></h3>
        </div>
        <div class="modal-body">
          <ul>
            <li><strong>Attribute:</strong> <%- attribute %></li>
            <li><strong>Created At:</strong> <%- created_at %></li>
          </ul>
        </div>
        <div id='task-modal-footer' class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>