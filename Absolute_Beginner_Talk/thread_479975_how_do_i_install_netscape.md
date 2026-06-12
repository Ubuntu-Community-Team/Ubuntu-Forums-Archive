---
title: "how do i install netscape?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-06-20
subquestion: is there a code to install from a URL?

i need to install netscape for a website that only uses ie and netscape for it's return management system.
how do i go about doing that?

---

### Post by Dr Small on 2007-06-20
You can get IE4Linux, from here:
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

Although it isn't netscape, it's IE...

Dr Small

---

### Post by thesonisshining on 2007-06-20
is there any way to avoid ie and use netscape instead? 
i DL'd it from their site but i don't know how to install it.

---

### Post by p_quarles on 2007-06-20
You can get the tarball straight from the Netscape homepage:
[http://browser.netscape.com/](http://browser.netscape.com/)

That said, Mozilla Firefox/Seamonkey are based on the Netscape platform, so should provide any functionality that Netscape does. If that doesn't work, I think the next thing to try would be to install Opera and use it to spoof Netscape. If that doesn't work, and only then, go ahead and get the tarball and compile it.

---

### Post by Dr Small on 2007-06-20
> **thesonisshining said:**
> is there any way to avoid ie and use netscape instead? 
i DL'd it from their site but i don't know how to install it.
It gives you a very detailed installation guide on how to install IE on Linux...
I find that would be your best bet, instead of compliing Netscape, or whatnot.

Dr Small

---

### Post by lahook on 2007-06-20
[http://browser.netscape.com/](http://browser.netscape.com/)
It's a "tar.gz" file
Linux

To install Navigator on Linux, extract the archive you downloaded and run ./netscape/navigator from a terminal. (This will execute the browser; there are no formal installation instructions available for Linux.)

---

### Post by Hitchhiker42 on 2007-06-20
I've had good luck using the Firefox extension "User Agent Switcher" to fool websites into thinking I'm using a different browser/OS. You can find it here: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by p_quarles on 2007-06-20
> **thesonisshining said:**
> is there any way to avoid ie and use netscape instead? 
i DL'd it from their site but i don't know how to install it.
You can compile the source code by doing this:

```
tar xvzf netscape-navigator-9.0b1.tar.gz
cd netscape-navigator-9.0b1
./configure
make
sudo make install
```

That said, I would really recommend those other options before you try this. Compiling from source can screw up your system sometimes.

---

### Post by RomeReactor on 2007-06-20
Hi. To install Netscape Navigator, first download it from [the official site]("http://ftp.netscape.com/pub/netscape9/en-US/9.0b/unix/linux/netscape-navigator-9.0b1.tar.gz"). Once it downloads, double-click on it to bring up File Roller; select "Extract". It will extract a folder named **navigator**. You can put that in your home folder, if you wish--I prefer to hide it by renaming it **.navigator** (notice the dot before the name). Now,  to launch it, you can do it from the command line (Terminal or by pressing ALT+F2), or by making a menu entry.

* To launch it from the command line:
```
/home/YOUR_USER_NAME/.navigator/navigator
```

To make an entry in the menu:
* Right-click on the menu and select "Edit Menus", select "Internet" on the left pane, and press "New Item". Now fill that out like this:
* Type: Application
* Name: Netscape Navigator
* Command: /home/YOUR_USER_NAME/.navigator/navigator
* Comment: Web Browser
The icon is located in **/home/YOUR_USER_NAME/.navigator/icons/mozicon50.xpm**

Hope this helps.

---

### Post by thesonisshining on 2007-06-20
```
tar: netscape-navigator-9.0b1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

---

### Post by NeoLithium on 2007-06-20
Or if you prefer it system wide, you can extract it in /usr/lib and then ```
sudo ln -s /usr/lib/navigator/navigator /usr/bin/navigator
```

Guess it just depends if you're the only user or not for the computer :)

---

### Post by NeoLithium on 2007-06-20
> **thesonisshining said:**
> ```
tar: netscape-navigator-9.0b1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Chances are it's on your desktop.  Type:
```
mv /home/YOUR_USERNAME/Desktop/netscape-navigator-9.0b1.tar.gz /home/YOUR_USERNAME/

then 

tar -xvzf netscape-navigator-9.0b1.tar.gz
```

---

### Post by p_quarles on 2007-06-20
> **thesonisshining said:**
> ```
tar: netscape-navigator-9.0b1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```
Then perhaps you have a different version, or one with a different name. Replace netscape-navigator-9.0b1 with whatever the actual name of the file you have is. Or try some of the other suggestions.

---

### Post by thesonisshining on 2007-06-20
> **RomeReactor said:**
> Hi. To install Netscape Navigator, first download it from [the official site]("http://ftp.netscape.com/pub/netscape9/en-US/9.0b/unix/linux/netscape-navigator-9.0b1.tar.gz"). Once it downloads, double-click on it to bring up File Roller; select "Extract". It will extract a folder named **navigator**. You can put that in your home folder, if you wish (I prefer to hide it by renaming it **.navigator** (notice the dot before the name). Now,  to launch it, you can do it from the command line (Terminal or by pressing ALT+F2), or making a menu entry.

* To launch it from the command line:
```
/home/YOUR_USER_NAME/.navigator/navigator
```

To make an entry in the menu:
* Right-click on the menu and select "Edit Menus", select "Internet" on the left pane, and press "New Item". Now fill that out like this:
* Type: Application
* Name: Netscape Navigator
* Command: home/YOUR_USER_NAME/.navigator/navigator
* Comment: Web Browser
The icon is located in **home/YOUR_USER_NAME/.navigator/icons/mozicon50.xpm**

Hope this helps.

ok this is going to sound incredibly dumb... but have patience. 
here is what i see in terminal
chris@christopher-desktop:~$
which part is my username; so that i do this right the first time.

---

### Post by thesonisshining on 2007-06-20
> **p_quarles said:**
> Then perhaps you have a different version, or one with a different name. Replace netscape-navigator-9.0b1 with whatever the actual name of the file you have is. Or try some of the other suggestions.

i have the same version but it didn't work.

---

### Post by thesonisshining on 2007-06-20
> **NeoLithium said:**
> Chances are it's on your desktop.  Type:
```
mv /home/YOUR_USERNAME/Desktop/netscape-navigator-9.0b1.tar.gz /home/YOUR_USERNAME/

then 

tar -xvzf netscape-navigator-9.0b1.tar.gz
```

it's hidden in my home folder; under .netscape/navigator

---

### Post by RomeReactor on 2007-06-20
> **thesonisshining said:**
> 
chris@christopher-desktop:~$
which part is my username; so that i do this right the first time.

it's **chris**:
```
**chris**@christopher-desktop:~$
```

---

### Post by thesonisshining on 2007-06-20
ok i got it working RR thank you for all of your help. GOD bless you.

---

### Post by atmartin50 on 2007-08-06
Hi Everyone,

I'm having trouble installing Netscape Navigator 9. I've followed the instructions found in this thread, but each time I extract the file and then try to launch the application via the Terminal, I either get a "segmentation error (core dumped)" message, or nothing happens at all. I've tried both version 9.0b1 and b2, but to no avail.

Could anyone help me out?

Many thanks in advance!

Aaron

---

### Post by RomeReactor on 2007-08-06
Hi. Are you running Ubuntu 64-bit? I don't have Navigator installed at the moment, but I think it's 32-bit only.

---

### Post by atmartin50 on 2007-08-07
No, I'm running a 32-bit version of Feisty.

---

### Post by atmartin50 on 2007-08-09
No need to reply, as I'm using Opera as my alternate browser. Thanks anyways.

---

### Post by stchman on 2007-08-09
> **thesonisshining said:**
> subquestion: is there a code to install from a URL?

i need to install netscape for a website that only uses ie and netscape for it's return management system.
how do i go about doing that?

Netscape and Firefox are functionally similar.  The website won't run with Firefox?

---

### Post by por100pre1 on 2007-08-09
> **stchman said:**
> Netscape and Firefox are functionally similar.  The website won't run with Firefox?

What's the benefit of using Netscape? :confused:

---

### Post by purebuilt on 2007-11-30
Rome,

You are close with this, but it is not working for me. What could be wrong?

DB

---

