KO3-Rest
========

Rest Module for Kohana Framework Version 3.2+

Dependencies
=========

1. No dependencies

Configuration
=========

###sign_request (bool)

Whether or not to attempt to validate incoming request signatures and append signature to outgoing requests.

Default: TRUE

###signature (Array)

Holds all config information used to compute signatures.

+ timestamp (string)
  - Index in incoming data and outgoing data to use for timestamp verification.
  - Default: timestamp  

+ public_key (string)
  - Index in incoming data and outgoing data to use for public_key verification.
  - Default: public_key  

+ signature (string)
  - Index in incoming data and outgoing data to use for signature verification.
  - Default: signature   

+ replaytimeout (int)
  - Time in seconds that a request must be made in, after creating a signature. This should allow for a small fluctuation in time between client and server.
  - Default: 60  

+ salt (string)
  - What salt to use for the PHP function mcrypt.
  - Default: $2a$10$ # Blowfish @ 10 Rounds No Extra Salt  

###debug (int)

At what Kohana evnironment level should the module start outputting debug information. 

    class Kohana_Core {
        // Common environment type constants for consistency and convenience
       const PRODUCTION  = 10;
    	const STAGING     = 20;
    	const TESTING     = 30;
    	const DEVELOPMENT = 40;
    }

Default: 40

###profile (bool)

If set to TRUE will add benchmarks to Kohana profiler.

Default: FALSE

Initializing Library
=========

Controller_Foo extends Controller_Rest

Receiving Request

You can use actions as normal

=========

  public function action_foo(){
  
  $object= new stdClass;
  $code=200;
  
  $this->respond($object,$code);
  
  }

HTTP Method Support

As above you can define a method that will accept all versions of a call ie action_foo, you can also make method specific versions to handle different types (ie  update/create)

=========

	public function action_put_foo(){}
	
	public function action_post_foo(){}
	

This allows you to override the default and also keeps you from building massive switches in your methods to support different behavior (thought thats ok if you want to do so)	

Authentication
=========


Send Response
=========


License
=========

This is licensed under the same license as Kohana
http://kohanaframework.org/license
This project is not endorsed by the Kohana Framework project.