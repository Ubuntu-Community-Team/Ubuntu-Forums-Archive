---
title: "configuring modules in apache?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by mikejstein on 2007-11-18
Hi all,
After spending several very confusing hours doing some web development, I finally realized that my server wasn't disabling caching.
After another confusing hour, I figured out how to install the expires and headers module.

I just have no idea how to actually configure them.  I'm trying to disable caching so I can code, deploy, and debug rapidly.

Any help would be greatly appreciated.

-Mike

---

### Post by Pinger05 on 2007-11-18
Not sure what you are referring to.  The server (to my limited knowledge) does not cache information.  The web browser does the caching.

Unless I am totally not understanding what you mean.

---

### Post by mikejstein on 2007-11-18
The server sets HTTPD headers in all the web pages it serves up.
In my case, I'm serving VXML pages that are being translated by [Voxeo's]("http://www.voxeo.com/") VXML servers.  I need to set the header on my pages so that they aren't cached by Voxeo.

---

