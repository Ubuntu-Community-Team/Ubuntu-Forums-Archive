---
title: "Running Scripts?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-29
How exactly do I run scripts? Sorry to be such a newbie. lol.

---

### Post by cmnorton on 2007-07-29
> **ukulele_ninja said:**
> How exactly do I run scripts? Sorry to be such a newbie. lol.
What kind of scripts do you want to run, and why?  I am assuming you would want to run bash scripts, which in themselves are a large topic, so more information would be helpful.

---

### Post by ukulele_ninja on 2007-07-29
Im not sure.... It is something that is supposed to install compiz. Does that help: [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

---

### Post by atomkarinca on 2007-07-29
it's already in the howto :)

> sh /path/to/file/CF Installer-Updater.sh

---

### Post by ukulele_ninja on 2007-07-29
> **atomkarinca said:**
> it's already in the howto :)

ryan@Ted:~$ sh /path/to/file/CF Installer-Updater.sh
sh: Can't open /path/to/file/CF
ryan@Ted:~$

thats what i get what when i typed it in.

---

### Post by atomkarinca on 2007-07-29
/path/to/file is the path where the script is. locate the script you downloaded then, say, it's in the /home/ukulele/downloads/compiz directory you should type:

sh /home/ukulele/downloads/compiz/CF Installer-Updater.sh

edit: and a quick reference:
open a terminal then after you write the directories (for this occasion it's /home/ukulele/downloads/compiz) then type CF and press tab button, otherwise it can be a little tricky.

---

### Post by ukulele_ninja on 2007-07-29
ok, its on my desktop so i typed: ryan@Ted:~$ sh /home/desktop/compiz-0.4.0/cf
sh: Can't open /home/desktop/compiz-0.4.0/cf

thanks for being patient and helping me i appreciate it, what am i not getting?

---

### Post by atomkarinca on 2007-07-29
it should be capital letters as far as i remember. i mean it's CF. and after typing CF press tab button and it should be completed automatically, then press enter.

and it's not a bother :)

---

### Post by ukulele_ninja on 2007-07-29
Alright, I apologize, im still learning all of this. I think I understand what you mean by making the directories, but how do I get tell it to go to that folder on my desktop?

---

### Post by atomkarinca on 2007-07-29
open a terminal window > type sh > then type /ho and press tab button (that's the easy way to get into folders :)) > then type Desk and press tab > type comp then press tab > type CF then pres tab > finally press enter. that should be about it.

---

### Post by ukulele_ninja on 2007-07-29
ryan@Ted:~$ sh
$ /ho
sh: /ho: not found

I got stuck there, thats the same error i got before only for a diff directory.

---

### Post by coffeeadikt on 2007-07-29
Strictly speaking you don't need to put in the full path to execute the script.

In your case, if you typed```
cd compiz-0.4.0
``` then ```
sh CF Installer-Updater.sh
``` it would work too.

There's another way to launch scripts that you will see from time to time by using a "./"

So ```
./CF Installer-Updater.sh
``` would work as well.

And just in case you're not aware of it, Linux has auto-complete in the terminal. Type the first few letters of what you want then press tab. It should automatically type out what's available until you need to make a choice. Pressing tab twice in a row will show you your available options from there.

---

### Post by atomkarinca on 2007-07-29
after typing /ho do you press the tab button? if yes, it should complete it to /home/ am i right?

---

### Post by ukulele_ninja on 2007-07-29
> **atomkarinca said:**
> open a terminal window > type sh > then type /ho and press tab button (that's the easy way to get into folders :)) > then type Desk and press tab > type comp then press tab > type CF then pres tab > finally press enter. that should be about it.


ryan@Ted:~$ sh
$ /ho   desk    comp    CF
sh: /ho: not found
$               

ugh this is difficult lol why cant it be easy?

---

### Post by ukulele_ninja on 2007-07-29
> **coffeeadikt said:**
> Strictly speaking you don't need to put in the full path to execute the script.

In your case, if you typed```
cd compiz-0.4.0
``` then ```
sh CF Installer-Updater.sh
``` it would work too.

There's another way to launch scripts that you will see from time to time by using a "./"

So ```
./CF Installer-Updater.sh
``` would work as well.

And just in case you're not aware of it, Linux has auto-complete in the terminal. Type the first few letters of what you want then press tab. It should automatically type out what's available until you need to make a choice. Pressing tab twice in a row will show you your available options from there.



ryan@Ted:~$ cd compiz-0.4.0
bash: cd: compiz-0.4.0: No such file or directory
ryan@Ted:~$     
Thats what happened with that one

---

