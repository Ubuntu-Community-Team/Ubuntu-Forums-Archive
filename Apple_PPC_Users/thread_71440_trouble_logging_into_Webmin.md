---
title: "trouble logging into Webmin"
date: 2005-10-03
forum: Apple PPC Users
---

### Post by anechoic on 2005-10-03
I installed Webmin, Webmin-core, and Webmin-slbackup from the Ubuntu rep and installed them...
one set of instructions stated to run the setup.sh script found int the /usr/share/webmin directory -- but there was none installed when I unpacked webmin...
having originally set this up last April I have forgotten how and where I got stuck until I tried it again today and found that I couldn't log into Webmin from the [https://127.0.0.1:10000](https://127.0.0.1:10000) URL...I changed the pswd using the perl script but still couldn't log in...so I retraced my steps and opened the /etc/webmin/miniserv.conf in a text editor and found most of it looked to have been set up correctly...
I also tried setting the ssl = 0 on the webmin server and rebooting the server with: /etc/webmin/stop; /etc/webmin/start
but still no luck in being able to log in
I'm using 'root' as the username and my new changepass.pl pswd as the pswd...
has anyone encounted this problem of logging into Webmin using UbuntuPPC 5.04? and if so, how did you manage to resolve them?
thanks in advance
KIM
Edit/Delete Message

---

### Post by Zimmer on 2005-10-03
# How do I change my Webmin password if I can't login?


with ubuntu  for the root user I did this:
sudo 
/usr/share/webmin/changepass.pl /etc/webmin root mypassword


and the address I use for webmin is  'http://localhost:10000/'
or  'https://localhost:10000/'  of course localhost should normally resolve to 127.0.0.1
The browser should then ask for user  (root)
and password  (mypassword)

So I hope you are only suffering from a fault in your syntax for the password change program....
Otherwise...I haven't a clue...

Regards

Zimm

---

