---
title: "[SOLVED] How can I install envy from the command line?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-23
I have a whit screen so using a live cd I did a fresh install and still have a white screen so I want to try envy to install the nvivia drivers.

---

### Post by Repent on 2007-06-23
1. Boot into recovery mode.
2. type sudo aptitude install Envy
3. type Envy -t
4. I picked install nvidia drivers, if you do this choose what ever driver you need.


I hope this helps

---

### Post by Crafty Kisses on 2007-06-23
> **ICUR2Ys said:**
> I have a whit screen so using a live cd I did a fresh install and still have a white screen so I want to try envy to install the nvivia drivers.

Have you always had this White screen?

---

### Post by ICUR2Ys on 2007-06-23
Repent:  Thank you I will give it a try and report back.

Codename:  No it was working with the restricted driver installed a couple of days ago, but it was acting funny, don't remember how exactly, but I unchecked restricted drivers to compare the generic driver and when I rebooted I had the white screen.

---

### Post by ICUR2Ys on 2007-06-23
I got the message:  Couldn't find any package matching "Envy".

---

### Post by Repent on 2007-06-23
Wow I'm sorry thats what worked for me now I have no idea, I wish you good luck with this.

---

### Post by BlahMan_of.Doom on 2007-06-23
Dude, it's envy not Envy.

---

### Post by Repent on 2007-06-23
lol my bad sorry.

 	1. Boot into recovery mode.
2. type sudo aptitude install envy
3. type envy -t
4. I picked install nvidia drivers, if you do this choose what ever driver you need.

---

### Post by ICUR2Ys on 2007-06-23
First I entered the command with Envy, then I entered the command with envy and I compared the error messages and they were the same.  I don't have the package.  I was hoping that there was a command that would download the package.

---

### Post by confused57 on 2007-06-23
> **ICUR2Ys said:**
> First I entered the command with Envy, then I entered the command with envy and I compared the error messages and they were the same.  I don't have the package.  I was hoping that there was a command that would download the package.
Here's a thread with basically the same question:
[http://ubuntuforums.org/showthread.php?t=448865&highlight=Envy](http://ubuntuforums.org/showthread.php?t=448865&highlight=Envy)

See the reply for using wget to download envy.

Added:  It looks like the latest envy is "envy_0.9.5-0ubuntu3_all.deb"

Here's how to install the .deb file:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by ICUR2Ys on 2007-06-23
Confused57 thank you.

I now have the desktop back.  The resolution is too low but I will work on that.  I don't remember all of the commands that I had to enter, but they were not all in this thread nor in the thread confused57 directed me to.  I found one in an error message and added that to the others then it worked.  It would be good if someone would put together a how-to from the wget thru running envy in text mode.  Oh,  the command that was not present in the above is:

sudo apt-get install -f

no packages referenced.

Thank you all I really needed the help, I really can't thank you all enough.  Your help was really appreciated.

---

### Post by confused57 on 2007-06-23
> **ICUR2Ys said:**
> Confused57 thank you.

I now have the desktop back.  The resolution is too low but I will work on that.  I don't remember all of the commands that I had to enter, but they were not all in this thread nor in the thread confused57 directed me to.  I found one in an error message and added that to the others then it worked.  It would be good if someone would put together a how-to from the wget thru running envy in text mode.  Oh,  the command that was not present in the above is:

sudo apt-get install -f

no packages referenced.

Thank you all I really needed the help, I really can't thank you all enough.  Your help was really appreciated.
Glad it worked...I had edited my reply with instructions on how to install from albertomilone.com website, which should get anyone started OK with downloading & installing envy.

---

### Post by ICUR2Ys on 2007-06-24
So you did my apologies I guess tunnel vision kept me from noticing the second reference.

I thank you  and the others that helped me.  I will collect the important parts of your references and store them on my computer so that they will be on hand in the future.

I still can't thank you enough.

---

### Post by Repent on 2007-06-24
Wow thats great, I hope everything works out for you.

---

### Post by confused57 on 2007-06-24
> **ICUR2Ys said:**
> So you did my apologies I guess tunnel vision kept me from noticing the second reference.

I thank you  and the others that helped me.  I will collect the important parts of your references and store them on my computer so that they will be on hand in the future.

I still can't thank you enough.

No apology necessary...I'm hoping anyone with a problem similar to yours can find this thread by searching the forum, and be able to download & install envy with the info provided...

---

