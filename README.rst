Attendly Node.js library
=======================

Node.js interface to the Attendly API

**Note: This is a very early alpha release of the api.. things may change**

Basic usage
````````````

.. code:: javascript

    //Include the Attendly API module path if not installed
    var attendlyAPI = require('./Attendly');
    //or if it is installed include the module by its name(Pending..)
    var attendlyAPI = require('Attendly');

    //Instantiate an Attendly class object
    var apiKey = '';
    var attendly = new attendlyAPI.Attendly(apiKey);

    // Login (normally you would just store the apikey and only login once)
    attendly.userLogin('username','password',function(error,data)
    {
        //In this callback funtion we can set the apikey to the Attendly class
        attendly.setAPIKey(data['result']['user']['apikey']);

        //Or reinstantiate the class sending the apikey in the constructor
        apiKey = data['result']['user']['apikey'];
        attendly = new attendlyAPI.Attendly(apiKey);
    }
    );

    // Get a list of events
    attendly.eventList(function(error,data)
    {
        data['result'].forEach(function(item){
                        console.log('Event name: ' + item['event']['name']);
                        });
    });

    // Get an event
    attendly.eventGet('id',function(error,data)
    {
        console.log('Event url:' + data['result']['event']['url']);
    });


Install via npm (pending..)
`````````````````

.. code:: bash

    $ npm install git://repository pending


Links
`````

* `website <http://attendly.com/>`_
* `documentation <http://attendly.me/apidocs/>`_
* `source <https://github.com/Attendly/attendly-nodejs>`_