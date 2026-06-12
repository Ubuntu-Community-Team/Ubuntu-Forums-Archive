---
title: "having trouble setting up wireless internet"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by rubykj on 2007-03-07
I just installed Ubuntu and it seems that I do not have network manager, niswrapper is not recongnized. I do believe that my card is compatible (Pro/Wireless 2200BG) but SYSTEM->Administration->networking does not seem to see it. Please help.
Yes I am a beginner and I am looking for some step by step troubleshooting
thanks a lot

---

### Post by endtroducing on 2007-03-07
Hi!

You dont need ndiswrapper with the ipw-2200. If you're on Edgy, it should work out of the box.

```
sudo iwconfig
```

It should be listed as eth1.

```
man iwconfig
```

is your friend.

Example with a 64 bit wep key

```
sudo iwconfig eth1 essid "foo" key 1234567869
```

E

---

### Post by rubykj on 2007-03-07
Yes thanks
I had done that earlier but no internet
eth 1 seems to see my card but I get an error of interface does not exist.
I have already seen the manual page before I came to the forum but I'm still not sure what to do 
Do you have any suggestions? I need more specific details than the manual. I do not think that I am understanding what needs to be done
thanks

---

### Post by rubykj on 2007-03-07
I do not believe I know the key
My internet just has a name?

---

### Post by rubykj on 2007-03-07
can I look up the key?

---

### Post by fmrmarineinbiz on 2007-03-07
Have you tried this solution?  It worked for me:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by rubykj on 2007-03-07
yes I've tried it
couldn't find package network-manager-gnome

---

### Post by rubykj on 2007-03-07
I had tried to install it and got an error of wireless tools not functional or not installed

---

### Post by rubykj on 2007-03-07
Does anyone have any suggestions on what I should do?

---

### Post by rubykj on 2007-03-07
While trying to configure network manager I get the error:
wireless-tools >= 28pre9 not installed or not functional

Please help
thank you

---

### Post by endtroducing on 2007-03-08
You probably need to install the wireless tools development files.

sudo apt-get install libiw-dev

Let me know if that solves it.

E

---

### Post by rubykj on 2007-03-08
error: couldn't find package libiw-dev package 
What do I do now?
Thanks for helping

---

### Post by endtroducing on 2007-03-09
Hi again,

Do you have libc6 and libiw28 installed?

---

### Post by rubykj on 2007-03-09
I dont know. How do I check and how would I install this?

---

### Post by fmrmarineinbiz on 2007-03-09
DUDE, are you running Dapper or Edgy???  I just upgraded to Edgy.  If youre not on Edgy, I'd suggest upgrading.  Download the Iso like for Dapper, and re install.  THEN, go back to my other post in this thread and re try what I suggested.  If you get the same error about not being able to find the package, make sure first that you have a direct internet line plugged into your computer, then in your terminal window type:  sudo apt-get update  .  THEN, after it does it's thing and gets the update packages (watch the terminal), re do the sudo apt-get install network-manager-gnome step as shown on that link in my post above.  It will now find that package for Edgy.  Finish up the steps, re boot, and you will be good to go.  (At least I was when I did so)

---

### Post by endtroducing on 2007-03-10
Do you have a connection to the internet with this pc? Like a wired connection?

E

---

### Post by HereInOz on 2007-03-10
That could be the problem.  Also, make sure that all the necessary repositories are enabled, to make sure that you can see, and download.  the applications which are suggested here.

Check out this: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories) if you are unsure of how to do this.

---

