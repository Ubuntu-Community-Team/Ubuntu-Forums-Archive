---
title: "getting optimal resolution on an Intel iMac"
date: 2006-07-31
forum: Apple PPC Users
---

### Post by irTESEV on 2006-07-31
So I'm giving linux a test run here on a 20" iMac.  I can't get it to run at the full screen resolution; doesn't give me the choice.  I've checked the forums and other places which tell me to run Synaptic, turn on Universe Repo, and install 915resolution.  Ran Synaptic Package Manager (which I am assuming is Synaptic) and I can't find Universe Repo or 915resolution.

How do I fix it?


**EDIT:** SOLVED.  I followed the directions in [this thread]("http://ubuntuforums.org/showthread.php?t=198453") and I got the acceleration I needed and the resolution came all by itself.  Awesome.  So if anybody is looking for a good how-to for getting acceleration in an Intel iMac or Macbook Pro, thats where you want to go.

---

### Post by avtolle on 2006-07-31
When you are in Synaptic; top menu bar, click on Settings; then, on Repositories (should be second/third one down); then, select all the repositories, including the Universe, click on Add; this will enable the Universe Repository. Then, while in Synaptic, click on Reload; after it finishes, run a search for 915resolution, and if there, select it to install it.

---

### Post by Seq on 2006-07-31
The 915resolution package will not provide the results you desire unless you have the educational intel imac with the Intel Graphics (or a non-pro MacBook, or Mac Mini). What you will likely need, unfortunately, is the proprietary ATI fglrx driver. You will also have to be using the bios functionality associated with bootcamp, as the ati driver requires a bios.

I have a MacBook, so cannot help too much on this, I'd suggest google and a search of the forums.

---

### Post by turtleJP on 2006-07-31
Here is what I've had to do in the past on the Wintel boxes. 

Open Terminal/Konsole

cd /etc/X11
sudo gedit xorg.conf or sudo kate xorg.conf (Kubuntu)

Add the resoulution to the list 
So I would add 1680x1050

Save the file and logout and restart the Xserver from the login screen.


Hope this works for you.

---

### Post by irTESEV on 2006-08-04
I figured it out.  As Seq said the 915resolution package was not what I wanted.  Also I need the acceleration so just adding the resolution "1680x1050" was not exactly what I wanted either.  After extensive searching I found [this thread]("http://ubuntuforums.org/showthread.php?t=198453") and it was exactly what I was looking for.  After I followed the directions the resolution appeared all by itself and I had the acceleration.  Perfect.  Thanx!!

---

