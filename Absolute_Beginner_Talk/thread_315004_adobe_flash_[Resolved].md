---
title: "adobe flash [Resolved]"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by jigglyj0 on 2006-12-08
i have no idea how to install the new adobe flash for my mozilla after downloading the stuffs..
super noobs here

---

### Post by taurus on 2006-12-08
Are you talking about flash 9 beta?  What is the name of the file that you just downloaded?

---

### Post by FreedomIsntFree on 2006-12-08
Flash 9 is now availible to *nix users.  It's about damn time right?  Anyways, go get it at [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

Here are instructions on installing it:

Download the file and save it wherever.
Navigate to the folder that it is in.
Type: gzip -dc FP9_plugin_beta_112006.tar.gz | tar x
Navigate into to folder it extracts.
Copy the file to your /home/USERNAME/.mozilla/plugins folder by typing:
cp libflashplayer.so /home/USERNAME/.mozilla/plugins
If you do not already have a plugins folder, type:
mkdir /home/USERNAME/.mozilla/plugins
Shutdown whatever browser you are using and restart it.  

If you are using Konqueror (like me) it should still pick up the plugin because it looks for them in there by default.

Hope that helps!

---

### Post by P235 on 2006-12-08
Thanks, Freedom, I have Flash running without problems.

---

### Post by ramlev on 2006-12-10
Im running kubuntu 6.10 x64bit. And i have done everything to the flash in firefox install text, but it's not working.

---

### Post by Famicommie on 2006-12-10
> **ramlev said:**
> Im running kubuntu 6.10 x64bit. And i have done everything to the flash in firefox install text, but it's not working.

There are solutions to lots of 64bit issues right here: [http://www.ubuntuforums.org/showthread.php?t=191205](http://www.ubuntuforums.org/showthread.php?t=191205)

---

### Post by HighD on 2006-12-10
> **FreedomIsntFree said:**
> Flash 9 is now availible to *nix users.  It's about damn time right?  Anyways, go get it at [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

Here are instructions on installing it:

Download the file and save it wherever.
Navigate to the folder that it is in.
Type: gzip -dc FP9_plugin_beta_112006.tar.gz | tar x
Navigate into to folder it extracts.
Copy the file to your /home/USERNAME/.mozilla/plugins folder by typing:
cp libflashplayer.so /home/USERNAME/.mozilla/plugins
If you do not already have a plugins folder, type:
mkdir /home/USERNAME/.mozilla/plugins
Shutdown whatever browser you are using and restart it.  

If you are using Konqueror (like me) it should still pick up the plugin because it looks for them in there by default.

Hope that helps!


Worked for me! Thanks Freedom :mrgreen:

---

### Post by ferg on 2006-12-10
Nice little guide there Freedom, thanks! All running nicely now :)

---

### Post by belovedconsole on 2007-03-11
I just had a really weird experience.  I'm running Ubuntu Dapper Drake, my first day.

On Myspace, it says, at the top, that I need the Adobe flash thing to view all media.

I click on it, go to Adobe, agree, and then when I get the downloads, there are two either us (tar) or other (redhat)

I choose tar and it gives me some weird error.

I research the forum, and someone says, "Restart Firefox."

I do that, click on the thing at the top again, get the same error.

But now I try something new.

I go to Michio Kaku's page on myspace, [www.myspace.com/mkaku](www.myspace.com/mkaku), and where there should be flash movies, there are blank spaces with a puzzle icon.

I click on one of these, and things seem to be suspended.

But now, the movies appear, at least, I can see the graphics, and it doesn't say I need a plugin.

I close Firefox.

I go back, this time to my page.  The music is playing, so I can stream audio.

I stop that.

All my video flash stuff shows that I don't need a plugin.

I press 'play' on one.

It starts playing, seamlessly.

Apparently, despite the error messages, I have downloaded and installed Flash for Ubuntu Linux.  The damn thing works.

I remember now, that this happened also with Kubuntu linux, which I was running from my laptop, as a test.  It actually took a lot longer than this, but ultimately, the damn thing was running, and I wasn't sure how.

It's as if there are protocols which tell you, according to old paradigms, that you're not really installing it, and that there are errors.

Yet meanwhile, in the background, you have already installed it.

I think on a very basic level developers have figured out how to make this happen, but the upper levels are still giving error codes as if it has not happened.

The code could simply check certain statuses.

In any event, I can play Adobe flash like it's nothing, and I didn't do anything, I didn't even have to unzip or untar or whatever it is, like I did in KDE, it just happened, by clicking on the movies, being disappointed, getting out of Firefox, and coming back.

I know this is not to helpful, except to give hope.  Perhaps someone more imbued with the system can tell us what exactly is going on here...

Again:

Click upper bar that says you need another plugin to show all media.

This will take you to Adobe website, with downloads.  Choose the tar.

It will give you an error.

Close down Firefox.

Go to [www.myspace.com/mkaku](www.myspace.com/mkaku).

Click on one of the blank videos that says you need a plugin.

Now try playing the videos.

Nothing.

Now exit out of firefox and go to [www.myspace.com/johnbrowning](www.myspace.com/johnbrowning), click on any youtube video (it should appear as shitty graphics with a "play" button super-imposed.

Notice that it plays.

This is what I did, I hope it works for someone.

---

