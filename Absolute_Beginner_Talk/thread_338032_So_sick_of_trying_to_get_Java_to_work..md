---
title: "So sick of trying to get Java to work."
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by vierdreieins on 2007-01-13
All I really want is a plugin for Java. I've tried installing Sun from the terminal, but I have no idea if it worked because I couldn't get any further when it brought up 'configuration' and the terms of service and it wouldn't let me do anything with it. 

After that, I tried installing the plugin, but it said it couldn't locate the file. I've been trying to get Java to work off and on for I don't know how long and it's beginning to get frustrating. I can't find it in Synaptic because whenever I search for something, the damn thing locks up.

Why can't there just be an add-on from Mozilla??? It always says it has to be done manually, and I wouldn't know how to go about doing that, obviously, because I'm an incompetent nincompoop who can't even install Java. ](*,)

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-13
Have you gone thru these directions already? 

[http://www.ubuntuforums.org/showthread.php?t=76702&highlight=how+to+install+java](http://www.ubuntuforums.org/showthread.php?t=76702&highlight=how+to+install+java)

As a last resort, you could always install Automatix and go from there... 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Let me know! 

Regards,

---

### Post by vierdreieins on 2007-01-13
> **k|d<FuNkY>FrY said:**
> Have you gone thru these directions already? 

[http://www.ubuntuforums.org/showthread.php?t=76702&highlight=how+to+install+java](http://www.ubuntuforums.org/showthread.php?t=76702&highlight=how+to+install+java)

As a last resort, you could always install Automatix and go from there... 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Let me know! 

Regards,

The problem with those directions is that whenever I download a file and then try to access it with the terminal, I must be doing something wrong because I just get an error. Am I supposed to be downloading the files somewhere specific? The other directions I read said that downloading them to the desktop is fine.

---

### Post by 4.9 on 2007-01-13
Administration > Synaptic Package Manager.

Search 'Java' on synaptic package manager and it should provide you with a plug in. Then just check the box and install.

---

### Post by vierdreieins on 2007-01-13
Oh, and I just noticed it in Automatix, so I'm trying that now (I always looked in multimedia and never saw it), so we'll see if it works.

---

### Post by vierdreieins on 2007-01-13
> **4.9 said:**
> Administration > Synaptic Package Manager.

Search 'Java' on synaptic package manager and it should provide you with a plug in. Then just check the box and install.

Searching locks it up. What is it under and what's the file specifically called?

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-13
Downloading the file to your desktop is fine... It's normally where I download the majority of my files... If you have a lot of files already on your desktop, you can certainly create a javaTemp file (*on your desktop*) and work within that particular directory. 

Let me know!

---

### Post by vierdreieins on 2007-01-13
Okay, Automatix came up with the configure thing again and I don't know what to do with it. Typing or pressing enter or anything doesn't work. Am I supposed to just ignore this? If so, it didn't work anyway.

---

### Post by vierdreieins on 2007-01-13
Perhaps it's installed and works, but just isn't connecting to Firefox. Should I need to do anything to get it working in my browser?

---

### Post by obsidion on 2007-01-13
> **vierdreieins said:**
> Searching locks it up. What is it under and what's the file specifically called?

  What do you mean searching locks it up. Do you have a really slow computer with very little ram ? are you too impatient ? what is the real problem here ?  You seem to be behaving like the proverbial chicken with its head cut off.

---

### Post by vierdreieins on 2007-01-13
> **obsidion said:**
> What do you mean searching locks it up. Do you have a really slow computer with very little ram ? are you too impatient ? what is the real problem here ?  You seem to be behaving like the proverbial chicken with its head cut off.

It stays locked for far too long and when I try to do anything it tells me to force quit. My RAM is all right, but nothing fancy. 

But the problem I actually care about is getting Java to work. I don't mean to seem like a beheaded chicken, I'm just trying to get some answers and posting when something else comes up.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-13
I think he might be just a little frustrated... No biggie, we're all willing to work with you... We just need your information to be a little more detailed if at all possible! 

So, first things first! Have you already installed Automatix? If so, once the Automatix app is launched, you should see this! 

[IMG]http://www.4moose.com/images/Screenshot-Automatix2 .png[/IMG]

Are you at this point yet? If not, and your having problems using Synaptic, please try the CLI

Let us know!

Regards,

---

### Post by vierdreieins on 2007-01-13
> **k|d<FuNkY>FrY said:**
> I think he might be just a little frustrated... No biggie, we're all willing to work with you... We just need your information to be a little more detailed if at all possible! 

So, first things first! Have you already installed Automatix? If so, once the Automatix app is launched, you should see this! 

[http://www.4moose.com/images/Screenshot-Automatix2 .png]("http://www.4moose.com/images/Screenshot-Automatix2 .png")

Are you at this point yet? If not, and your having problems using Synaptic, please try the CLI

Let us know!

Regards,

Yes, I have Automatix and just got [this]("http://img.photobucket.com/albums/v240/scarlet-tear/Screenshot4.png"). Should I be able to do anything with it, because it's just been sitting here open for a while.

---

### Post by obsidion on 2007-01-13
Ok let's try this, you said you downloaded from sun
 Note your sudo password is your own as long as you are the first created user on the system.


So presumably you have saved to your desktop

open a terminal, you don't say whether you are using gnome or kde in your profile and what version you are running, note setting this helps us to help you.

once in the terminal cd Desktop
there you will find something like jre-1_5_0-linux-i586.bin
type chmod a+x jre-1_5_0-linux-i586.bin

this makes it an executable file

now sudo ./jre-1_5_0-linux-i586.bin

  It should install and might ask you some questions, pay attention and answer them.
Use tab to navigate to the ok or hit y depending on the question and your system.

 Now once that is running you need to find the firefox/mozilla plugins and symlink them

Mine installed to

/usr/lib/j2se/1.4/jre/plugin/i386/mozilla

so I go to my firefox plugin directory
in my case /usr/lib/firefox/plugins

and set up a symlink to the java plugin

sudo ln -s /usr/lib/j2se/1.4/jre/plugin/i386/mozilla//usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin.so

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-01-13
You'll need to agree to the license terms and conditions before it's proceeds with the install... Click the 'tab' button on your keyboard and then hit 'Enter' -- If you've already done this, is it still hanging on ya? The install should move forward fairly quickly! I don't believe JAVA is too big of a file to install! If the system seems unresponsive, I'd kill the process and try and run it again...

Let me know!

---

### Post by obsidion on 2007-01-13
> **vierdreieins said:**
> It stays locked for far too long and when I try to do anything it tells me to force quit. My RAM is all right, but nothing fancy. 

But the problem I actually care about is getting Java to work. I don't mean to seem like a beheaded chicken, I'm just trying to get some answers and posting when something else comes up.


  If you are using synaptic, it is asking you a licence question so you need to click the terminal mode or however your install words this in the progress bar. It hasn't locked up, you just didn't know what to do, it is a bit anal at this point and it took me a while to click to waht was happening here too :)

---

### Post by vierdreieins on 2007-01-13
All right, I think I got it working. You guys helped immensly, thank you!

---

### Post by vierdreieins on 2007-01-13
> **obsidion said:**
> If you are using synaptic, it is asking you a licence question so you need to click the terminal mode or however your install words this in the progress bar. It hasn't locked up, you just didn't know what to do, it is a bit anal at this point and it took me a while to click to waht was happening here too :)

I haven't been using it much because of the lockup thing, but it doesn't come up with a licensing question when I use it--it just locks up. So I've been sticking to Add/Remove and Automatix if I can, unless I can find it by browsing the folders.

---

