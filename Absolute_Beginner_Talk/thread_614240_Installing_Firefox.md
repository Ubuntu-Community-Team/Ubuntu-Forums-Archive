---
title: "Installing Firefox"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-15
I have FireFox 2.0.0.6 and I have just downloaded 2.0.0.9, one problem Im not sure how to install the new version, can someone help me?

---

### Post by ThrobbingBrain66 on 2007-11-15
Use Ubuntuzilla...it's a script written by a member of the forums that will do everything for you.

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by RobotoWorks on 2007-11-15
Thanx, but is there another way incase I cant get this to work?

---

### Post by ThrobbingBrain66 on 2007-11-15
It's the easiest method there is.  But here is a method for manual install:
[https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29#head-a18df3338b868ce5f14336fd2ee58ce6b5d574b2](https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29#head-a18df3338b868ce5f14336fd2ee58ce6b5d574b2)

What version of Ubuntu are you running?  If you have Feisty or Gutsy, you should have Firefox 2.0.0.8

---

### Post by RobotoWorks on 2007-11-15
Oh its Gutsy, then I guess I have 2.0.0.8. The problem with it is, when I try to install FireFox theme, for every theme I try I get the "Not compatible with your FireFox version" message, I want to fix this so I thought upgrading might fix it.

---

### Post by jfinkels on 2007-11-15
Read the link in my signature on installing software.

I believe that when you download a firefox release, they give you a .tar.gz package with all the libraries and executables you need to run it, so all you do is extract it ```
tar xvzf firefox-2.0.0.9.tar.gz 

```
Change into the directory it created:```
cd firefox
```and then run it:```
./firefox
```
I think.

---

### Post by RobotoWorks on 2007-11-15
> **jfinkels said:**
> Read the link in my signature on installing software.

I believe that when you download a firefox release, they give you a .tar.gz package with all the libraries and executables you need to run it, so all you do is extract it ```
tar xvzf firefox-2.0.0.9.tar.gz 

```
Change into the directory it created:```
cd firefox
```and then run it:```
./firefox
```
I think.

I have the tar.gz file but when I try to use the first code here the message I get

tar: firefox-2.0.0.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by jfinkels on 2007-11-15
You have to be in the directory into which you downloaded the file. So do a 'cd' to change to the directory that contains the file. For example:```
cd Desktop
```if it is on your desktop. Then type "tar xzvf " and press tab to view a list of possible filename completions. Start typing "fir" then press tab and bash should automatically complete the name of the file.

---

### Post by RobotoWorks on 2007-11-15
Thanx, but is there a sudo code for it?

---

### Post by jfinkels on 2007-11-15
"sudo" is just a command that lets you run programs as the super user without having to log in as the super user. There is no need for it here. Read the link in my signature about Root & Sudo.

---

### Post by RobotoWorks on 2007-11-15
Thanx, how do I install 2.0.0.9 using synaptic?

---

### Post by RobotoWorks on 2007-11-15
Can it be done through synaptic?

---

### Post by rsambuca on 2007-11-15
> **RobotoWorks said:**
> Can it be done through synaptic?

No.

---

### Post by RobotoWorks on 2007-11-15
Okay, I'll quit trying to upgrade but can someone give me a list of Linux compatible FireFox themes becuase the many Ive tried before are not compatible.

---

### Post by rsambuca on 2007-11-15
> **RobotoWorks said:**
> Okay, I'll quit trying to upgrade but can someone give me a list of Linux compatible FireFox themes becuase the many Ive tried before are not compatible.

There is no such thing.  If an extension is compatible with version 2 Firefox, it will work with linux or Windows versions.  What exactly is it that you are trying to install?

---

### Post by RobotoWorks on 2007-11-15
This one [https://addons.mozilla.org/en-US/firefox/addon/5246](https://addons.mozilla.org/en-US/firefox/addon/5246)

But when I try to install it it says "Not compatible for FireFox 2.0.0.8, in fact all the themes Ive tried have said that

---

### Post by rsambuca on 2007-11-15
Weird.  It works perfectly on my system, although I really don't like that theme!

Anyways, what version does it say when you go to "Help -> About Mozilla Firefox"?

---

### Post by RobotoWorks on 2007-11-15
2.0.0.8

---

### Post by rsambuca on 2007-11-15
Was this just a default ubuntu install?

---

### Post by RobotoWorks on 2007-11-15
Yep, and thats why I want to change the theme its ugly!

---

### Post by Paul820 on 2007-11-15
Just thought i would say the theme installs for me fine as well, running firefox 2.0.0.8, and you are right about the theme rsambuca, ewwwwww:)

---

### Post by rsambuca on 2007-11-15
Maybe try reinstalling firefox (you can just use Synaptic for this).

---

### Post by RobotoWorks on 2007-11-15
Can you please to me how to reinstall?

---

### Post by rsambuca on 2007-11-15
Open your Synaptic Package Manager.  Go to 'firefox' and right-click it.  There should be an option to Reinstall somewhere in there.

---

### Post by RobotoWorks on 2007-11-15
Thanx, can you give me some nice dark themes that should be compatible for my FireFox version?

---

### Post by RobotoWorks on 2007-11-16
Anyone?

---

### Post by rsambuca on 2007-11-16
Is it working now?

And please do not bump your posts so quickly.  It is better etiquette to wait a day prior to doing so.

---

### Post by RobotoWorks on 2007-11-16
Thanx for the tip, I am reinstalling 173 FireFox packages so its taking a while to finish...

---

