---
title: "Installed Squeezecenter but doesn't appear in Applications list"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by jbh1 on 2008-03-08
Hi - can anyone help?  Sorry for the newbie question...

I  have installed Slim Devices Squeezecenter (the new version of Slim Server) on my computer running Ubuntu 7.10.

I had to use the Synaptic Package Manager to do this, and it thinks the software is installed ok.

However I can't see it in the Applications menu and can't figure out how to access it.

Any advice much appreciated

---

### Post by buntu_Geek on 2008-03-08
The problem is that its not displayed in the Applications menu ...

You have to edit your mani menu..
you can do this by going to:
System-->Preferences-->MainMenu

There select the category of your application from the left frame 
And then select the check box corresponding to your application on the right to enable that application to be displayed in your menu...

Hope that helps..

---

### Post by jbh1 on 2008-03-08
Thanks very much for your suggestion.  Unfortunately, when I look in the System/Preferences/Main Menu window, the application does not appear in the right hand "Items"  pane no matter which category I click on in the left hand "Menus" pane.

I tried uninstalling squeezecenter and installing slimserver instead.  Again, the Synaptic Package Manager thinks it is now installed - but I can't find it anywhere.

I'd be hugely grateful for any further advice.

---

### Post by buntu_Geek on 2008-03-08
I am not sure with installing an application from Synaptic.....
Coz. synaptic resolves only dependencies for a particular package and not the whole application....

So i suggest you to use add or remove programs and search for the application from the search bar available there....

---

### Post by jbh1 on 2008-03-09
OK, I tries that, but still could not see the slimserver application evewn when "all available applications" was selected and the location Slim Devices give themselves for the software - deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main -  was incuded in my software sources list.

Could it be something wrong with the software package whih means it just doesn't appear properly in ubuntu - or am I just doing something wrong still ....?

---

### Post by jbh1 on 2008-03-09
OK,  I tried installing a different application (which is something I should have tried before).  This time VLC - and I managed to install that with no problems.  So I know I am following the correct procedure for installing software.  Presumably this means the problem must lie with the Slimserver package - so I will wait to hear back from their technical support, who I have also asked about this.

Thanks again for your help.

---

### Post by buntu_Geek on 2008-03-09
Hey check this download link for u r application...

The official website:
[http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)

And also check the slimdevice forum's thread:
[http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)

Hope that helps.. :D

---

### Post by doug1212 on 2008-03-09
Hi,
SqueezeCenter will not appear in apps menu, no need as it is a browser based app.
Just add:
```
deb http://debian.slimdevices.com stable main
```
to your sources.list and do:
```
sudo apt-get install squeezecenter
```
this should sort out any dependencies.

All admin is done by opening a browser and entering:
```
localhost:9000/
```

Doug.

---

### Post by jbh1 on 2008-03-09
Thank you so much Doug.  I had totally failed to realise that Slimserver operates through a browser.  I said I was a newbie !

I'm immensely grateful to you.

---

### Post by jr1414 on 2008-05-21
Ok, I'm a newbie too.  I tried this and when I try to going through the browser I get a cannot connect to server error.

Is there something else I can try?

Thanks.

---

### Post by clump on 2008-05-31
Maybe it will help, but here's what I did.  

First, try restarting it and check the logs:
```
sudo /etc/init.d/squeezecenter restart
sudo cat /var/log/squeezecenter/server.log
```

If it doesn't start then something is wrong with squeezecenter.  For me there were already lots of errors in that file (see below), but the actual  stop/start of slimserver didn't report any errors.

Check that mysql is running
```
sudo /etc/init.d/mysql status
```

If there are errors then there's your problem.  I saw no errors.

Point a web browser to [http://127.0.0.1:9000](http://127.0.0.1:9000). Still couldn't connect.

Check the server logs again
```
sudo cat /var/log/squeezecenter/server.log
```

There were multiple complaints about not being able to connect to MySQL.  Some searching and this turned out to be useful:

[http://http://bugs.slimdevices.com/show_bug.cgi?id=7580#c1]("http://http://bugs.slimdevices.com/show_bug.cgi?id=7580#c1")

There are various things to check and try there.  I have a fresh Ubuntu 8.04 install and most of those things seem to be already done. I only had to do the following to get squeezecenter up and running:

```
sudo /etc/init.d/squeezecenter stop
sudo mv /etc/apparmor.d/usr.sbin.mysqld.squeezecenter.orig /tmp
sudo /etc/init.d/apparmor restart
sudo /etc/init.d/squeezecenter start
```

There are still some warnings (and a different error) in the server.log but it works.

---

