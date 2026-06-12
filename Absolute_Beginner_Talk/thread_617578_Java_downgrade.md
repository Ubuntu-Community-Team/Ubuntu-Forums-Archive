---
title: "Java downgrade"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by kstump on 2007-11-19
Looks like there may be a basic problem in the current Java add on. I'm not running gaming software but I am having a similar that the program I want to run does not work with the installed version of Java. The software vendor has told me that it needs Java 1.5 to operate.  Can anyone write a basic treatise on getting 1.6 out and 1.5 back in? I'm going on week four in trying to get this thing to run and I'm about ready to throw the whole computer out the window of a 20 story building!!!!!!! (or just go back to windows until UBUNTU gets things ready for us normal computer workers)

---

### Post by rbc on 2007-11-19
I had a similar problem getting LogMeIn to work. It didn't like Java 1.6 either. You can try this and see if it works.
Close the application you're trying to run. Go to Synaptic and search for java. Select "completely remove" java common. It will want to remove some additional things as well, and that's OK. Without closing Synaptic, so another search for java 5. Select sun-java-fonts, and sun-java5-plugin. Again, it will want to install some additional things. click apply and let things install. 
restart your application and see if that helps.

---

### Post by rsambuca on 2007-11-19
You can have more than one version of java installed on your rig.  You can switch which version you are running by entering this command in a terminal```
sudo update-alternatives --config java
```

---

### Post by kstump on 2007-11-19
OK people, let's remember where we are. Absolute beginner. I've tried uninstalling and reinstalling, however, apparently I don't know how to do that correctly either since it didn't work.  As far as using the terminal command to say which version I want to use.......HUH????

I don't think this software is ready for the majority of computer users yet.

---

### Post by rsambuca on 2007-11-19
OK, no problem.  Let's start at the beginning and keep this simple.

What version of Ubuntu are you using?  32bit, or 64bit?  Gutsy?

What is the program that you are trying to run that requires java?

---

### Post by philinux on 2007-11-19
you only have to copy and paste the command into the terminal hardly rocket science

---

### Post by kstump on 2007-11-19
As far as I know, 32 bit Gutsy.  And as near as I can tell from other posts, I need to remove the java I have now and install 1.5  it's just no one has explained how to go about this.  ThinkorSwim trading desktop is the program I want to run, but it won't even install without the Java RE it wants.  Thanks

---

### Post by rsambuca on 2007-11-19
I don't think there is a linux version of that.  Isn't it Windows and Mac only?

---

### Post by kstump on 2007-11-19
No, they have a Linux version which after downloading you type the command sh ./thinkorswim_installer.sh  and then it's supposed to load up and run. Unfortunately it keeps failing because it won't run with the JrE of 1.6, which is what I have and can't seem to get rid of. I saw another post that says it works with 6.3 also. Either way I can't seem to get rid of the 1.6 and install something else.

---

### Post by kstump on 2007-11-19
Everything is "rocket science" if you don't know what to do or how to do it!  Why do you think they call this the "absolute beginner talk"?

---

### Post by rsambuca on 2007-11-19
Have you tried downloading the new java?  You just download it to someplace (usually somewhere easy to find, such as your Desktop).  It is a self installing binary, meaning you just click on it after downloading and it should do everything for you.

If you want to remove your existing java first, you can do it via the Synaptic Package Manager.  Go to your top menu bar and select "System -> Administration -> Synaptic Package Manager".  You will want to select 'sun-java6-jre' (and/or 'sun-java5-jre).  Just right click and select "complete removal".

Then try the new java and then the ThinkorSwim.  

Good luck, and let us know how it goes.

---

### Post by kstump on 2007-11-20
The removal seems to have worked fine. The installation did not. I had to mess around with it to get it to "self install". After I finally got it to go it was .....guess what ....1.6 again.  The sudo command you gave me earlier returns nothing after the new install.

Guess I'll go back to windows, not the Vista windows, I already upgraded to XP from that.

---

