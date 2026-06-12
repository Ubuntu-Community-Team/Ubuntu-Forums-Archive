---
title: "apache, fcgi, and rails.."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by confuciusquinn on 2006-09-20
I'm getting a really weird problem. I try any url (e.g. "http://192.168.1.100/rails/info/properties") and It returns this:
"#!/usr/bin/ruby1.8
#
# You may specify the path to the FastCGI crash log (a log of unhandled
# exceptions which forced the FastCGI instance to exit, great for debugging)
# and the number of requests to process before running garbage collection.
#
# By default, the FastCGI crash log is RAILS_ROOT/log/fastcgi.crash.log
# and the GC period is nil (turned off).  A reasonable number of requests
# could range from 10-100 depending on the memory footprint of your app.
#
# Example:
#   # Default log path, normal GC behavior.
#   RailsFCGIHandler.process!
#
#   # Default log path, 50 requests between GC.
#   RailsFCGIHandler.process! nil, 50
#
#   # Custom log path, normal GC behavior.
#   RailsFCGIHandler.process! '/var/log/myapp_fcgi_crash.log'
#
require File.dirname(__FILE__) + "/../config/environment"
require 'fcgi_handler'

RailsFCGIHandler.process!"

in the browser.
=/
This is the contents of 'dispatch.fcgi' which means the .htaccess is working just fine but for some reason apache is interpreting dispatch.fcgi as a regular text files. how do i get it to interpret it as an fcgi script??
I'm using fcgid instead of regular old fastcgi. I have this line
"AddHandler fcgid-script .fcgi" 
in what seems to be a dozen different apache config files. I haven't seemed to put in the right one yet apparently. Anyone have any thoughts? 

thanks.

---

