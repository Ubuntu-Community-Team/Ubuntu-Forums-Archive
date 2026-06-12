---
title: "tomcat 5 Problem"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Ranganaths on 2007-03-24
I have just installed the tomcat5 from synaptic manager and set the java_home. but when i start the server. its as follows
..
ranganaths@Gizmo:~$ sudo /etc/init.d/tomcat5 start
Starting Tomcat 5 servlet engine using Java from /usr/lib/jvm/java-6-sun/bin: ranganaths@Gizmo:~$


when i say the status of the server it says as follows :
ranganaths@Gizmo:~$ sudo /etc/init.d/tomcat5 status
Tomcat 5 servlet engine is not running.


before installint tomcat 5 i was able to run apache2 but now even thats not running.. its giving this error as follows
anganaths@Gizmo:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

please let me know whts wrong with this

Thank you

---

