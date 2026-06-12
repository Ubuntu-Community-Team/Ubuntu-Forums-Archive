---
title: "apache wont run - httpd wont run"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by mielie007 on 2007-04-19
hi

i have been trying for the past couple of days to get apache to run again.

everything seems to look fine, but when i tell apache to restart i get the following error.

=ROOT=:/etc/tmp/httpd-2.2.4# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                         
httpd (pid 19044?) not running
                                                                               [ ok ]

when i check to see what processes are running on my server, httpd is not there. 

what do i do to fix it? please help.

---

### Post by PilotJLR on 2007-04-19
The process shows up as "apache2", which is unlike red hat systems.

So to see if it's running:
```

ps -ef | grep apache2

```

---

### Post by mielie007 on 2007-04-20
I used ps-ef | grep apache2 and there is nothing that appears that is related to appache. 

I can figure out why it doesn't want to start the httpd demon, or any demon related to apache.

Please will you help me figure out what is wrong with apache ](*,)

---

### Post by PilotJLR on 2007-04-21
Let's try to manually start and restart apache... please post the output of the following:

```

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
sudo tail /var/log/messages

```

My hope is that something incriminating will post to the logfile...

---

### Post by mielie007 on 2007-04-23
Let's try to manually start and restart apache... please post the output of the following:

Code:

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
sudo tail /var/log/messages

My hope is that something incriminating will post to the logfile...

hi 

here is the output you wanted.

```

# /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server...                                            httpd (pid 3833?) not running
                                                                         [ ok ]
# /etc/init.d/apache2 start
 * Starting apache 2.0 web server...                                     [ ok ]
# tail /var/log/messages
Apr 23 18:55:17 Dapper-Drakie -- MARK --
Apr 23 19:00:01 Dapper-Drakie syslogd 1.4.1#18ubuntu6: restart.
Apr 23 19:15:17 Dapper-Drakie -- MARK --
Apr 23 19:35:17 Dapper-Drakie -- MARK --
Apr 23 19:55:18 Dapper-Drakie -- MARK --
Apr 23 20:00:01 Dapper-Drakie syslogd 1.4.1#18ubuntu6: restart.
Apr 23 20:15:18 Dapper-Drakie -- MARK --
Apr 23 20:35:19 Dapper-Drakie -- MARK --
Apr 23 20:55:19 Dapper-Drakie -- MARK --
Apr 23 21:00:01 Dapper-Drakie syslogd 1.4.1#18ubuntu6: restart.




```

---

### Post by PilotJLR on 2007-04-27
Wow, I'm seeing nothing at all bad in there.

Just to double check.. if you open a browser on that machine and navigate to [http://localhost](http://localhost), what do you get?

If you don't have a browser on the server, then just use any machine ON YOUR LAN and point to the server's ip address.

If no luck there, then how about this:
```

sudo tail /var/log/apache2/error.log

```

---

### Post by mielie007 on 2007-05-07
hay thanks for all your help.

i got it running again. i updated my ubuntu to the latest one and it updated apache to and now its running again.

i think the reason it stopped working was because i created a new user group and pointed apache away from the default to the new user group. this was maybe what caused it to stop working....:lolflag: 

but its running now.

thanks again.:KS

---

