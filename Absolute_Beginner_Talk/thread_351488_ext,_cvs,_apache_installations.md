---
title: "ext, cvs, apache installations"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Ranganaths on 2007-02-02
Hi guys,

         I just wanted to know if it is possible to have  webserver say tomcat or apache for executing both python web applications and java applications? 
      Secondly is it possible to use  the server type "ext" connect to the remote Repository in the CVS? 

      and how to start ssh server in Ubuntu.. 

Thank you

---

### Post by hmLyons on 2007-02-03
Check out  [this page from the ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server") and also [this thread]("http://ubuntuforums.org/showthread.php?t=297900&highlight=ssh+server") for lots of info about running SSH.

I am not aware of any webserver that will run Python and Java Servlets. What you can do however is run Tomcat and Apache on different ports so that you could access the servers like [http://localhost:8011/SomeJavaServlet](http://localhost:8011/SomeJavaServlet) and [http://localhost:8022/somePythonScript.py](http://localhost:8022/somePythonScript.py)

It's very easy to do.

Hope that's helpful.

---

