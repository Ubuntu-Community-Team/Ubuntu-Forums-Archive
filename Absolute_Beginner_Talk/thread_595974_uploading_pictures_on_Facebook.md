---
title: "uploading pictures on Facebook"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Yuliya on 2007-10-29
I try to upload pictures on [www.facebook,com](www.facebook,com) and I get this message:

[http://www.facebook.com/editalbum.php?aid=5145&add=1](http://www.facebook.com/editalbum.php?aid=5145&add=1) wants to load an applet.

GNU Classpath's security implementation is not complete.

HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!

Click "Cancel" if you do not trust the source of this applet.

Click "Trust Applet" to load and run this applet now.

Click "Trust Applet and Add To Whitelist" to always load and run this applet from now on, without asking.

The whitelist is a list of the URLs from which you trust applets.

Your whitelist file is " /home/yuliya/.gcjwebplugin/whitelist.txt ".

It doesn't matter what I click, I still get the same thing and can't upload anything. What can Id o?

---

### Post by gdoutch on 2007-10-29
You have Java installed?

---

### Post by WinterWeaver on 2007-10-29
what Browser are you using?

That doesn't look like a firefox error... is it Epiphany or Galeon?

---

### Post by Yuliya on 2007-10-29
I have Firefox but you're right that it doesn't look the usual error message. It's bigger - the kind of add that sometimes comes out and says "You've won the lottery!" (or something like that) and I have no idea whether I have Java installed or not

---

### Post by gdoutch on 2007-10-29
You need Java for the Facebook upload application.

Check in synaptic and install it if you need to.

---

### Post by Yuliya on 2007-10-29
but I have Java and I still get that message I posted

---

### Post by madscientist032 on 2007-10-29
> **Yuliya said:**
> but I have Java and I still get that message I posted

There is a work-around for uploading pictures to Facebook.  When you are at the 'upload new pictures' page, there should be a section towards the bottom of the page that looks like this screenshot:[IMG]http://i109.photobucket.com/albums/n45/madscientist032/Troubleupload.png[/IMG]

Click on the link after the "having trouble" question. That should help.

---

### Post by Yuliya on 2007-10-29
it worksssssssssssssss!!!
Thank you so much!

---

### Post by gdoutch on 2007-10-29
Yaaay! Good for you!

---

### Post by SurrealWraith on 2008-02-03
Yes, the secondary method of uploading pictures works, but I still have the same problem when trying to use any Java applet on Firefox.  No matter what I click, the window will not load. Anyone know how to fix this?

---

### Post by Auslegung on 2008-02-23
I'm having an identical problem, I have the most up-to-date java everything, I pass the test on the java website, and yes I can use the alternate method of uploading pictures but I'd rather not for two reasons 1) takes long as hell 2) it logs me out after I upload photos for the first time of any Facebook session.  Any other ideas?  Is it possible that the Ubuntu Firefox version just doesn't play nice with Facebook (I know nothing about programming and don't know if that suggestion is asinine or not).

---

### Post by ToSsMaStR on 2008-03-19
I have exactly the same prob, i have java installed, using firefox on gutsy, but the applet just does not load? and fixes?

---

### Post by sr4794 on 2008-05-18
I fixed this irritating problem by actually checking which java bits and bobs I had installed via synaptic package manager.

I noticed that although I had sun-java6-jre installed, I didn't have sun-java6-plugin.

Once I had installed this component the facebook photo java applet magically worked.

Make sure you have the following installed...

sun-java6-jre
sun-java6-plugin

Pure revision avoidance.

---

### Post by unc0nn3ct3d on 2008-06-26
Icedtea was definitely causing the problems here, removed any trace of it from the system and everything worked like a charm

---

