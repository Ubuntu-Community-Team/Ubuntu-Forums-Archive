---
title: "How to Switch Profiles in Thunderbird"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-21
I have multiple profiles loaded in my Thunderbird application. In order to switch from one to the other, someone told me I have to use the Profile Manager. As I understand, the Profile Manager only runs through a terminal window. Here below are the instructions from the Mozilla website for how to start the Profile Manager in a terminal window, but even following these instructions I could not get the Profile manager to open.

Here are the website instructions:

> Close the application completely and  make sure that it is not running in the background. Open the terminal and execute cd (program directory) then execute:

    * (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 

Alternately, in a terminal type the path/to/firefox-mozilla-thunderbird -profilemanage 

So I executed the order below:

swarup@swarup-laptop:~$ /home/swarup/.mozilla-thunderbird -profilemanager
bash: /home/swarup/.mozilla-thunderbird: is a directory

What do I have to do to open Profile Manager?

---

### Post by kellemes on 2007-08-21
> **swarup said:**
> I have multiple profiles loaded in my Thunderbird application. In order to switch from one to the other, someone told me I have to use the Profile Manager. As I understand, the Profile Manager only runs through a terminal window. Here below are the instructions from the Mozilla website for how to start the Profile Manager in a terminal window, but even following these instructions I could not get the Profile manager to open.

Here are the website instructions:

 

So I executed the order below:

swarup@swarup-laptop:~$ /home/swarup/.mozilla-thunderbird -profilemanager
bash: /home/swarup/.mozilla-thunderbird: is a directory

What do I have to do to open Profile Manager?

".mozilla-thunderbird" is a directory indeed.
You have to find the executable that actually runs when you startup thunderbird..
I don't know where Ubuntu stores it (I'm on another system), could be in /usr/bin or somewhere in /opt/..

And then you do: "/path/to/probably_mozilla_thunderbird -profilemanager"

---

### Post by stevebakerj on 2007-08-21
[QUOTE=swarup;3226592
What do I have to do to open Profile Manager?[/QUOTE]

How do you start Thunderbird? With an Icon on the desktop or through an Icon on the Applet panel?

Either way just right click on the desktop Icon and select proerties, click on the application tab and add " -profilemanager" to the end of the Command: line.

If you use the Icon on the applet panel again right click on the Icon select 'Configure Thunderbird Button' then select the Application Tab and amend the command line as above.

---

### Post by philinux on 2007-08-21
If you dont want to mess with the normal launcher then in terminal, dont change directories just type,

mozilla-thunderbird -profilemanager

---

### Post by swarup on 2007-08-21
> **stevebakerj said:**
> How do you start Thunderbird? With an Icon on the desktop or through an Icon on the Applet panel?

Either way just right click on the desktop Icon and select properties, click on the application tab and add " -profilemanager" to the end of the Command: line.

If you use the Icon on the applet panel again right click on the Icon select 'Configure Thunderbird Button' then select the Application Tab and amend the command line as above.

Thanks A Lot for your reply.
I couldn't follow it all the way, but I can see your instruction is going to lead me to the solution once I understand it.

I use an Icon on the desktop to start Thunderbird.

I was following you until you wrote, "click on the application tab". Do you mean the "Applications" tab at the top of the desktop screen? 

The overall meaning I took away from your message (perhaps I am wrong?) was to use the start-up icon as a way to get the correct pathway for the executable onto the command line. So I right-clicked on the Thunderbird desktop icon, selected "copy", and then pasted it onto the command line. That gave me the pathway. To which I then added " -profilemanager". Here is the printout of my output from terminal:

```
swarup@swarup-laptop:~$ /home/swarup/Desktop/mozilla-thunderbird.desktop -profilemanager 
bash: /home/swarup/Desktop/mozilla-thunderbird.desktop: Permission denied
```

Is it almost correct? What do I need to add-- a "sudo" somewhere or something?

---

### Post by swarup on 2007-08-21
> **philinux said:**
> If you dont want to mess with the normal launcher then in terminal, dont change directories just type,

mozilla-thunderbird -profilemanager

That sounds great! So easy!

The only problem is, I tried it and it doesn't seem to work. Did I do it wrong somehow?

Here's what I typed, along with the terminal window's reply:

```
swarup@swarup-laptop:~$ mozilla-thunderbird-profilemanager
bash: mozilla-thunderbird-profilemanager: command not found
```

---

### Post by philinux on 2007-08-21
You had no space in between 

mozilla-thunderbird    -profilemanager :lolflag:

---

### Post by stevebakerj on 2007-08-21
No sorry I didn't quite explain properly. I am _**not**_ using the terminal, I am editing the command string for the Icon on your desktop so close the terminal.

Make sure Tb is NOT running.

Then right click on the Icon and select 'Properties' The select the 'Application' Tab The edit the Command: Line by adding " -profilemanager" (without the quotes) to the end of what is already their it will most likely look like this after amending if you have a default installation.

thunderbird % -profilemanager  or  thunderbird -profilemanager

---

### Post by swarup on 2007-08-21
> **philinux said:**
> You had no space in between 

mozilla-thunderbird    -profilemanager :lolflag:

It worked! You were right. 

Such a simple command. Why is it that EVERYWHERE one seeks instruction for this-- including Mozilla's own website (see my first post), they give complex instructions where you have to type out all the pathways etc. Why don't they just tell you what you told me? That would have been enough.

Now, one last question: is going into a terminal window the only way to open Profile Manager? Or is there a way to set up a GUI on the desktop for it?

---

### Post by swarup on 2007-08-21
> **stevebakerj said:**
> No sorry I didn't quite explain properly. I am _**not**_ using the terminal, I am editing the command string for the Icon on your desktop so close the terminal.

Make sure Tb is NOT running.

Then right click on the Icon and select 'Properties' The select the 'Application' Tab The edit the Command: Line by adding " -profilemanager" (without the quotes) to the end of what is already their it will most likely look like this after amending if you have a default installation.

thunderbird % -profilemanager  or  thunderbird -profilemanager

In my computer when one selects 'Properties', then no such 'Application' Tab appears. There IS a tab called "Launcher". And in that window there is a "Command" window in which is written:

mozilla-thunderbird

I am guessing that may be the window you mean. So if in that window I append

 " -profilemanager" (without the quotes)

then I think it'll automatically open the profile manager whenever I click on the start-up icon. Right?

==> Yes. I've tried it, and that does the job. Thanks very much. It is an excellent solution.

---

### Post by philinux on 2007-08-21
> **swarup said:**
> It worked! You were right. 

Such a simple command. Why is it that EVERYWHERE one seeks instruction for this-- including Mozilla's own website (see my first post), they give complex instructions where you have to type out all the pathways etc. Why don't they just tell you what you told me? That would have been enough.

Now, one last question: is going into a terminal window the only way to open Profile Manager? Or is there a way to set up a GUI on the desktop for it?

Simple

right click anywhere on you desktop and select create launcher

Name - whatever you want
Command = mozilla-thunderbird -profilemanager (same as you typed in terminal - I guess the complication may arise from setups with different user etc maybe)

works on mine anyway

---

### Post by swarup on 2007-08-22
> **philinux said:**
> Simple

right click anywhere on you desktop and select create launcher

Name - whatever you want
Command = mozilla-thunderbird -profilemanager (same as you typed in terminal - I guess the complication may arise from setups with different user etc maybe)

works on mine anyway

I see. That is very helpful to know. Thanks very much.

---

### Post by skubisnack on 2008-03-12
I also just found this:

[https://nic-nac-project.de/%7Ekaosmos/index-en.html#profname](https://nic-nac-project.de/%7Ekaosmos/index-en.html#profname)

It is an extension that allows you to switch profiles from within Thunderbird.  I had been looking for this extension ever since I switched from Windows and just stumbled upon it the other day.  I hope it helps.

-G$

---

