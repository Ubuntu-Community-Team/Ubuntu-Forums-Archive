---
title: "Installing or extracting a .deb..."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jezebel on 2007-03-05
Hi...

Very new here and first experience with Linux. 

I just installed Ubuntu, all went well.

Now I am following some instructions on how to fix my Japanese Input system. This link here - [https://help.ubuntu.com/community/JapaneseInput ]("https://help.ubuntu.com/community/JapaneseInput")- provides most of the information I need , except...

Here's the instructions I was following:

[INDENT]Note: This will not work in edgy or above, because the uim_anthy script is missing due to a [WWW] packaging bug. To work around, download the [WWW] dapper-package and then type the following in a terminal in the directiory where you saved the package:[/INDENT]

I downloaded the Dapper script, saved it to my desktop. But now what?:( 

I don't understand what it means to open a terminal in the directory...and when I opened the terminal and tried to follow the directions anyway, I keep getting the message that the file or folder couldn't be found.

Any help at all would be much appreciated. I am so very new to all this and I apologise for taking up your time.

---

### Post by bapoumba on 2007-03-05
> **jezebel said:**
> 
I downloaded the Dapper script, saved it to my desktop. But now what?:( 

> type the following in a terminal in the directory where you saved the package:
If the package is on your desktop, you need to go to that directory first:
```
~ $ cd Desktop/
```
Then your prompt should look like this:
```
user@host:~/Desktop $ 

```
And you can follow the tutorial from there.

---

### Post by Jussi Kukkonen on 2007-03-05
Your desktop is actually a directory called "Desktop" under your home directory. To move into it, issue this command:
```
cd ~/Desktop
```
(the ~-sign is a shorthand for */home/yourusername*).

---

### Post by Drakkor on 2007-03-05
Have you tried just double-clicking the .deb file that should bring up the package install program !

---

### Post by jezebel on 2007-03-05
Thanks - giving me the code to get to the desktop was very very helpful. I think I got somewhere - but now I don't know were:confused:  

I was still trying to follow these directions:

[INDENT]dpkg -x uim-anthy_1.0.0-1ubuntu1_i386.deb uim-package
sudo cp uim-package/etc/X11/xinit/xinput.d/uim_anthy /etc/X11/xinit/xinput.d/uim_anthy

It will set the default input method for your user account and you current language, but you can set it for a given language session. For example, you could use:

im-switch -z fr_FR -s uim_anthy

to associate the uim-anthy input method to the French session of your account.

uim allows you to type traditionally, so you can also launch im-switch as administrator to set the default input method for all the users without any side effect:

sudo im-switch -s uim_anthy

Note that user settings prevail over the system ones, so a user you can always override the default input method. [/INDENT]

The link for this is [here.]("https://help.ubuntu.com/community/JapaneseInput") 

So, I tried and this is what I am now getting

tracy@Tracy-Sotec:~$ sudo im-switch -s uim_anthy
No system wide default defined just for locale en_ZA .
Use "all_ALL" quasi-locale and set IM.
update-alternatives: Cannot find alternative `/etc/X11/xinit/xinput.d/uim_anthy'.

tracy@Tracy-Sotec:~$ 


Sorry - I really don't know what I'm doing...

By the way - yes, I did think to double-click the package, but it wouldn't open because "there is a newer version already installed"; except that the newer version is missing one very important piece to the puzzle...

---

### Post by bapoumba on 2007-03-05
@ jezebel: sorry I will not be able to help you out with this. May be others will ;)
Have you contacted the person who wrote this wiki page ?

---

### Post by jezebel on 2007-03-07
Thanks for the help; maybe I will contact the wiki-writer...

For now at least I have a work-around - the SCIM will at least work in the text editor; I can then copy and paste to the browser, etc.Add new information
EDIT: It's working! I followed the instructions on [this wiki]("https://wiki.ubuntu.com/Japanese_input_and_font_setup"), and now...&#26085;&#26412;&#35486;&#12364;&#12391;&#12365;&#12383;&#65281;
[URL="https://wiki.ubuntu.com/Japanese_input_and_font_setup"]
https://wiki.ubuntu.com/Japanese_input_and_font_setup[/URL]

---

