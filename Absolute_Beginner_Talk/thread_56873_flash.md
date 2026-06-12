---
title: "flash"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by shibainucan on 2005-08-14
I just installed ubuntu yesterday.   I noticed an immediate problem with multimedia.  No flash plug-in was installed.   I went to synaptic to install one.  I found a flashplayer-mozilla.  I figured that would work with firefox.  But no, it wouldn't work. crashed firefox.

So I fixed my repositories (to get more programs listed).  I found the Macromedia flash plugin  (called flashplugin-nonfree).  That didn't crash firefox.  But I had no sound.  Someone on the forum advised doing the following command on the terminal  (sudo ln -s /user/lib/libesd.so.0  /usr/lib/libesd.so.1

That worked!  now I have flash no crash with sound!  However, I have to ask. 
 Should an absolute beginner have to go through all that? Should this all be pre-installed?

---

### Post by aysiu on 2005-08-14
Two issues here:

1. I don't think your experience is typical. Firefox didn't crash when I installed flash. And I never had sound issues.

2. Nonfree software cannot be included with Ubuntu because of Ubuntu's free/free philosophy (free software, free cost). If you like nonfree software included with Linux, you should try Mepis, Blag, or Linspire.

---

### Post by shibainucan on 2005-08-14
Let me explain.  Firefox didn't always crash.  Only when I went to a specific site (the weather network).  But that is my favorite weather site.  I go there often.  If you go there you might have the same problem  ([http://www.theweathernetwork.com/](http://www.theweathernetwork.com/))

For some reason, the mozilla version of flash wouldn't work.  The Macromedia version of flash didn't crash firefox, but no sound.  The "symbolic link" fix is to fix a bug in the Macromedia version (apparently).

---

### Post by az on 2005-08-14
[QUOTE=shibainucan]
That worked!  now I have flash no crash with sound!  However, I have to ask. 
 Should an absolute beginner have to go through all that? Should this all be pre-installed?[/QUOTE]


That fix only works for a small percentage of people.  The sound system had many bugs.  The next version of Ubuntu (October) should have them all fixed, so no, not even an expert should have to go through that.  

The point is that when you run into a problem, think about filing a bug report so that it is fixed for others.

Thanks!

---

### Post by aysiu on 2005-08-14
[QUOTE=shibainucan]Let me explain.  Firefox didn't always crash.  Only when I went to a specific site (the weather network).  But that is my favorite weather site.  I go there often.  If you go there you might have the same problem  ([http://www.theweathernetwork.com/](http://www.theweathernetwork.com/))[/QUOTE] I just went there, and it didn't crash. In fact, as far as I can tell, there's no Flash on the Weather Network's homepage...

Sorry. Went back to the page. There is Flash, but it's an advertisement.

---

### Post by TristanMike on 2005-08-14
[QUOTE=azz]That fix only works for a small percentage of people.  The sound system had many bugs.  The next version of Ubuntu (October) should have them all fixed, so no, not even an expert should have to go through that.  

The point is that when you run into a problem, think about filing a bug report so that it is fixed for others.

Thanks![/QUOTE]How do you know if it's a bug or just me being a stupid user?? I've always had a problem acertaining where my issues come from, me being an idiot, or an actual bug, how do I know?

---

### Post by az on 2005-08-14
[QUOTE=TristanMike]How do you know if it's a bug or just me being a stupid user?? I've always had a problem acertaining where my issues come from, me being an idiot, or an actual bug, how do I know?[/QUOTE]

Really good question.

Probably a good rule of thunb is to spend ten minues looking for another user with the same problem by searching the forums and then another five minutes looking through the current bug reports to see if there is already one filed.  When in doubt, ask on IRC, the -devel mailing lists, or here (in that order of importance).

---

