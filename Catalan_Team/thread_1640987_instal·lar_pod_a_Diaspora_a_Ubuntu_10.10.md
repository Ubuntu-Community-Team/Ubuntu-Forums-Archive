---
title: "instal·lar pod a Diaspora a Ubuntu 10.10"
date: 2010-12-08
forum: Catalan Team
---

### Post by franz666es on 2010-12-08
Hola, he instal·lat el Diaspora al meu Maverick i no sé com he de configurar un pod extern a config/app_config.yml, com per exemple el següent 

[LIST]
[*] [http://diasp.eu]("http://diasp.eu/") [IMG]https://assets0.github.com/img/ae503f3dd7f1f80f0a832392448ea844c3a45285?repo=&url=http%3A%2F%2Fdiasp.eu%2Fapple-touch-icon.png&path=[/IMG]

[LIST]
[*]Opened: 30/11/2010
[*]Updated: major changes
[*]Maintained by a private person
[LIST]
[*][http://twitter.com/diasp_eu](http://twitter.com/diasp_eu)
[/LIST]
 
[*]Operating system: Linux
[*]Comments: Public and free Diaspora pod for Europe
[/LIST]
[/LIST]

Si algú em pot donar un cop de mà, gràcies!

Us indico el contingut del app_config.yml per si no el teniu instal·lat

#   Copyright (c) 2010, Diaspora Inc.  This file is
#   licensed under the Affero General Public License version 3 or later.  See
#   the COPYRIGHT file.

default:

  # Hostname of this host, as seen from the internet.
  pod_url: "http://localhost:3000"

  # Set this to true in order to close signups.  Users will still be
  # able to invite other people to join.
  registrations_closed: false

  # Enable extensive logging to log/{development,test,production}.log
  debug: false

  # Websocket server setup, see script/websocket_server.rb
  # Enable extensive logging to websocket server.
  socket_debug : false

  # Websocket host, leave as 0.0.0.0 unless you know what you are doing
  socket_host: 0.0.0.0

  # File containing pid of running script/websocket_server.rb
  socket_pidfile: "log/diaspora-wsd.pid"

  # Websocket port, should normally be 8080 or 8081.
  socket_port: 8080
  socket_collection_name: 'websocket'

  # Secure websocket confguration (wss://)
  # requires SSL cert and key
  socket_secure: false
  socket_private_key_location: '/full/path/to/file.key'
  socket_cert_chain_location: '/full/path/to/cert_chain.crt'

  # Diaspora is only tested against this default pubsub server.
  pubsub_server: 'https://pubsubhubbub.appspot.com/'

  # Host/port for running mongodb server. See also mongodb.conf
  mongo_host: 'localhost'
  mongo_port: 27017

  # Setting this to true enables diaspora's "send email" functionality
  # requiring meaningful smtp_* settings. These are options for RoR's
  # ActionMailer class.
  mailer_on: false

  # Address/port to smtp server handing outgoing mail.
  smtp_address: 'smtp.example.com'
  smtp_port: '587'

  # Domain administered of smtp server.
  smtp_domain: 'example.com'

  # Sender address in diaspora's outgoing mail.
  smtp_sender_address: 'no-reply@joindiaspora.com'

  # Authentication required to send mail. Use one of 'one','plain',
  # 'login' or 'cram-md5'. Use 'none' if server do not support
  # authentication
  smtp_authentication: 'plain'

  # Credentails possibly required to log in to SMTP server if
  # smtp_authentication != 'none'
  smtp_username: 'smtp_username'
  smtp_password: 'secret'

  #google analytics key, if false, it won't include the javascript
  google_a_site: false
  
  #piwik integration if not set, no javascript included
  piwik_id: 
  # the site url in raw format (e.g. pikwik.examplehost.com)
  piwik_url: 
  

  #cloudfiles username and api-key, used for backups
  cloudfiles_username: 'example'
  cloudfiles_api_key:  'abc123'
  invites_off: false

development:

test:
  pod_url: "http://example.org/"
  socket_port: 8081

production:

---

