---
title: "Is there a concept of uninstall?"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-25
I know, immediate responses will probably be 
apt-get --purge remove <insert software here>

But I am talking about completely uninstalling stuff, so that I can start again. I messed up some Apache2 and PHP configurations when playing with Drupal (which I couldn't get to work anyway) and I want to start again. However, apt-get --purge remove apache2 php4 and reinstalling has changed apparently nothing on my system. An earlier post here helped me figure out that if I wanted something removed, I need to search what package installed it in the first place. For example, I want to completely remove mysql and start afresh. Is there anyway? In Windows all I had to do was uninstall and I was back where I  started all good to go.

And remember, this is on a server machine (testing) and so it has no GUI. I do all the work SSHing from another machine on the same subnet.

---

### Post by chimera on 2005-12-25
start gnomedesktopsearch, search for the name of the application you want to remove, then delete all the files it finds that you find relevant to that application (after you removed it with apt)

always worked for me

---

### Post by bscbrit on 2005-12-25
There is no program that I can find called 'gnomedesktopsearch'.  

If there was one, surely it would be a GUI program?  The original post specified he is running a server machine (i.e. no desktop) and so he couldn't use this program anyway.

---

### Post by harisund on 2005-12-25
Yes, I couldn't find a gnome-desktop-search as well. Besides if necessary I could run GUI through SSH tunnel...

---

### Post by bscbrit on 2005-12-25
harisund

When you say that you want to "completely uninstall stuff and start again", I assume that you are referring to a single or small number of packages?  Otherwise, wouldn't a completely new Ubuntu installation achieve the same thing?

When you do a 'apt-get remove', what is being left behind?

---

### Post by bscbrit on 2005-12-25
"this is on a server machine (testing) and so it has no GUI"

I don't think that any GUI program is so important that I would consider installing the whole GUI just to run it!  You are correct in what you say, that a GUI could be run through SSH, but I suspect that the 'find' command would be the underlying program being used by a GUI and you already have access to that on your server.

---

### Post by hbush on 2006-01-10
Hi guys I think we have a problem here which we can not get it.. its not same as in winxp. uninstall then manually delete the files. 
I have the same problem I tried all above the result is: the config files are not changed. 
Q: what is left on: apt-get --purge remove apache2 
A: everything and while rebooting I see the error red line regarding apache 

I might have another problem and I think its that. After installing apache2 the folder is locked ...I'm not the owner how comes? please feel free to loagh I just cant get it. 

Now since I have completely removed the /etc/apache2 folder, when I reinstall everything goes fine, no error msgs but the apache2 folder is not there. 
doh  :confused: 
please help ..

---

### Post by jerrykenny on 2006-01-10
I reckon you dont need to uninstall for your particular problem ie misconfiguration . . . .

I think you just need to find the configuration files,  and they're probably hidden, . . . but within your home folder somewhere . . . 

In a terminal, try         slocate      *.conf    or slocate     *.config

Actually that'll find dillions of files, but you get the gist . . . 

Just delete the offending file, then next time you launch the prog, it'll reconfigure itself.

---

### Post by hbush on 2006-01-10
thanx for the tip and the reply jerrykenny,

the problem is that following the above posts I have already deleted the Apache2 folder and some config files. (I assume I shouldn't)
now when I run sudo apt-get instal apache2 nothing happens (the installation procedure terminates normally)

---

### Post by harisund on 2006-01-10
Ok everyone .. here is the deal .. 

1. When you install a package (irrespective of the platform you are working on) the package will require some dependancies. Basically some libraries which it needs to run. For example, let's assume package A depends on B, C and D, and another package F depends on G, H and C. Pictorially -> 
A => B, C, D
F => G, C, H

2. The beauty of apt-get is that if you ask it to install package A, it automatically installs B, C, D first and then installs A. That is what makes Synaptic and Ubuntu so popular, the famed "One click software installation methods." 

3. The problem occurs when you want to start from a scratch. You uninstall A and then reinstall A but some changes you made seem to continue. For example, you purged apache2 (--purge remove apache2.) but then you find that the config files remained. The thing is, when you purge a package, you are deleting, uninstalling whatever only that particular package and not the dependancies. In other words, you purged package A. But why did the config files remain? because they belong to package B on which A was dependant !

Do you get what I am saying? In other words, when you changed your config files you were changing files of package B and so when you purged Apache2 you were uninstalling package A. Hence the config files didn't change and hence your reaction 
> Q: what is left on: apt-get --purge remove apache2 
A: everything and while rebooting I see the error red line regarding apache 

The reason "everything" was left behind was of course you never uninstalled them !

I think you would have realized why --purge remove A doesn't uninstall packages B, C and D as well because some other package might depend on them (or might not too.) If apt-get decides to remove B, C and D because you wanted it to remove A, then package F breaks because C is no longer available !!!

*Anyway the straight forward, to the point answer (shortening all my lectures) is that the config files you edited are a part  of the apache2-common package and not apache2 package, so you need to --purge remove apache2-common to make sure your config files vanish. *

What I did as a work around was a script that would call apt-get, identify all the packages that it was installing, and reinstall them if I needed to "start from scratch." That way the answer to your question will be 
Q. What is left after I run my script to uninstall? 
A. Nothing !

---

### Post by hbush on 2006-01-12
Harisund, thank you very much for the clear explanation. This should be a sticky and the first thing which should be read by newbees like me, who run from win to linux. Now, for me is very clear how apache functions. 

I had no idea regarding these dependencies and that's why I couldn't understand why nothing works. 

Wish I have read this first then do what I've done but no harm. Im learning on mistakes. I reinstalled ubuntu and now I started over... everything works fine. Thank you all.

---

### Post by harisund on 2006-01-12
Here are a couple of other things you might want to keep in mind: 

1. All Linux settings are stored in ASCII files, and they are generally well documented. You can simply read the comments and proceed to edit them to your convenience. 
2. Since you can so easily edit these settings (basically the REGISTRY of the Linux world) you should always be making backups of these files, so that if you b0rk your system bad, you can always log into the rescue mode (during boot time) and copy back the previous file that you had saved and overwrite your settings, so that things get back to normal. It is best to keep a log of what you do. Essentially you never need to reinstall..
3. The dpkg command (a level lower than apt-get too) is a very powerful one. Here are 2 features that you might want to use .. 

dpkg -L packaganame
Lists all the file that the package installed on your system. 

dpkg -S filename
Lists the package which installed filename in your system. 

Following our example: 

Let's see what apache2 installed on our system:
dpkg -L apache2

And since we are most likely to have edited something inside the /etc/apache2 folder, let's see which package installed that folder in the first place. 
dpkg -S /etc/apache2

This will tell you what you need to purge. Also, in case you just want to restore the default settings, you can either do --purge remove and then a install, or a 
dpkg-reconfigure packagename. 

uninstall-reinstall  and dpkg-reconfigure command basically do the same thing.

---

