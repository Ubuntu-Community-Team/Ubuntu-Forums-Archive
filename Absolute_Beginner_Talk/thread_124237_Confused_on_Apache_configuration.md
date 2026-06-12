---
title: "Confused on Apache configuration"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-02-01
I'm trying to configure Apache - and am getting conflicting instructions:

I've Apache 2.0.53 installed on Ubuntu Hoary 5.04.

The readme file in /etc/apache2 says apache2.conf is the main configuration file and httpd.conf is an empty file.

I opened them both and this seemed to be the case - the text in httpd.conf said it was there only for backwards compatibility reasons and apache.conf was full of text that looked important.
Also the readme says conf.d is a good place to stick additional configuration directives.

BUT.... looking at the Apache [website](http://httpd.apache.org/docs/2.0/configuring.html) it says that httpd.conf is the main config file.:confused: :confused: Other websites/tutorials etc say this also.

So what am I missing? I can't believe that the Apache people have arsed up their own webpage or that the Apache I got with Ubuntu has included the wrong readme in the package - so I must be getting the wrong end of the stick somewhere.

Should I stick my changes in httpd.conf, apache2.conf or even the conf.d file?

BHT

---

### Post by hen3rz on 2006-02-01
> BUT.... looking at the Apache website it says that httpd.conf is the main config file.  Other websites/tutorials etc say this also.


the httpd.conf file is the only config file for apache under windows, hence the reason why all the tutorials use httpd.conf instead of apache2.conf. this is also why it says that the httpd.conf is included for backwards compatibility reasons.

> Should I stick my changes in httpd.conf, apache2.conf or even the conf.d file?


apache2.conf should be fine and so should httpd.conf it doesnt matter really either way works. Not to sure about conf.d though.

> So what am I missing? I can't believe that the Apache people have arsed up their own webpage
I dont think that would happen in a million years and if it ever did it would be picked up within minutes of it being available online.

---

### Post by MJN on 2006-02-01
httpd.conf has been used by Apache for all its versions, whether that be for Unix, Windows etc etc. This hasn't changed...
 
..however the Debian port of Apache has strayed to a modularised configuration approach. Thus it is only Debian-based Apache's that utilise apache2.conf hence why the Apache documentation still says httpd.conf.
 
As mentioned above you can use either (there is an include statement in apache2.conf to parse the config from httpd.conf) however if you're here to stay (in the land of Debian) then go with the flow and use apache2.conf...
 
Mathew
 
P.S. Site-specific/virtual server config is now stored in sites-available/* - read what's already in there along with the relevent READMEs/HowTo's and you'll be away.

---

### Post by Bubba Ho-Tep on 2006-02-01
Ahhhhhh, it all makes sense now. Thanks guys.

BHT

---

