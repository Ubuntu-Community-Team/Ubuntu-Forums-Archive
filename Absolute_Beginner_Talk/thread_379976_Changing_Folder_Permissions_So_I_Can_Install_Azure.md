---
title: "Changing Folder Permissions So I Can Install Azureus Plugins."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2007-03-09
Ok.
So unlike the windows version of Azureus that has a plugin wizard, this version does not have one. 
So I did some research and found out that plugins should be put here:
/home/grammatrain/.azureus/plugins/azplugins
But of course this folder is read only and in order to change it where it is no longer read only I need to be logged in to root.
So I started looking for commands to over ride this but I have found no luck. 

I have tried both of these and it hasn't work:

sudo chown -R grammatrain /home/grammatrain/.azureus/plugins


sudo chgrp -R grammatrain /home/grammatrain/.azureus/plugins

I'm not really sure why, it should have worked I think.
Any kind soul care to help me?

---

### Post by igknighted on 2007-03-09
Anything in /home/<your_username> you should have write access to.  There should be no need chown anything.  What is the result of "ls -a /home/grammatrain/.azureus/plugins/azplugins"?

---

### Post by Famicommie on 2007-03-09
You need to chmod the files, not chown them.

sudo chmod 666 ~/.azureus/plugins

---

### Post by osc1882 on 2007-03-09
igknighted, I get this:
"
.  ..  azplugins_2.1.1.jar  plugin.properties
"

I'm not sure what that means, but that's what it says.

---

### Post by Famicommie on 2007-03-09
> **osc1882 said:**
> igknighted, I get this:
"
.  ..  azplugins_2.1.1.jar  plugin.properties
"

I'm not sure what that means, but that's what it says.

I think he meant to ask you to issue the command:

```
ls -al ~/.azureus/plugins/azplugins
```

The -l switch will show read/write/executable permissions.

When I issue that command, I get the output 

```
lrwxrwxrwx 1 fami fami 36 2007-01-27 23:17 azplugins -> /usr/share/azureus/plugins/azplugins
```

If you aren't getting the lrwxrwxrwx part EXACTLY like that, then you can fix everything with the command

```
chmod 777 ~/.azureus/plugins/azplugins
```

Hope that helps.

*note: ~ means the same thing as /home/<user>

---

### Post by igknighted on 2007-03-09
thnx fami, that indeed was what I intended.

---

### Post by Remthewanderer on 2007-03-26
I am running into the same issue as the original poster.  I chmod the plugins folder but I still do not see the installation wizard from the plugin drop down menu.

Now when I try to open Azureus the program will open and close right away.

I have tryed uninstalling and reinstalling Azureus through the package manager but I am still running into the same issue.

Any help getting this working correctly would be appreciated SO much!

Thanks!

---

### Post by Roger Mathisen on 2007-09-26
sudo these commands...

chmod 777 /home/<your-user-dir>/.azureus/plugins
chmod 777 /opt/azureus/plugins
chmod 777 /opt/azureus/azupnpav/plugin.properties


This worked for me. Thanks to readable error-messages...

---

### Post by djwhiplash on 2007-09-26
> I am running into the same issue as the original poster. I chmod the plugins folder but I still do not see the installation wizard from the plugin drop down menu.

Now when I try to open Azureus the program will open and close right away.

I have tryed uninstalling and reinstalling Azureus through the package manager but I am still running into the same issue.

Any help getting this working correctly would be appreciated SO much!


Just had the exact same problem.  There is a workaround here:

[https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/68020]("https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/68020")

There's a lot to read through but if you go to Mike Fedyk's post on the 2007/03/19 and follow that it helped me out.  Once the prog is up and running go into options and disable "show animated error messages" in the logs section

Hope this helps

Cheers

---

