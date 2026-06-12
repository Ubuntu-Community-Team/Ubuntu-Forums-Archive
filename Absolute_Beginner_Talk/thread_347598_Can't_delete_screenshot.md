---
title: "Can't delete screenshot"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-01-27
Here we go again guys, the noob needs some help. I took a screenshot of sometning I needed to send out in an email. Mission accomplished. Now I want to delete it from the desktop where I saved it, but when I click on it I get the error:
"The Application "nautilus" has quit unexpectedly."
It shows as a smallish rectangular popup that doesn't want to go away. By repeatedly clicking close it does eventually leave and the screenshot goes with it, but when the computer is restarted the screenshot is back. I am using Dapper Drake. Any suggestions?

---

### Post by r4ik on 2007-01-27
Try,

sudo nautilus

and delete the file.

---

### Post by paydaydaddy on 2007-01-27
> **r4ik said:**
> Try,

sudo nautilus

and delete the file.

sorry to be a pain, but I am a noob in the purest sense of the word. An example of script to enter into the terminal would probably save me from turning this into an hours long process. Please?

---

### Post by paydaydaddy on 2007-01-27
I opened a terminal and entered "sudo nautilus" and got the following result:

"(nautilus:21037): Gtk-CRITICAL **: gtk_table_attach: assertion `GTK_IS_WIDGET (c hild)' failed"

along with is came the hard to close poopup telling me that nautilus has quit unexpectedly.

---

### Post by max.diems on 2007-01-27
Type Alt+F2. You will get a window called "Run Application" with a one-line text input. Type "gksudo nautilus". Press enter. If you are asked for a password, enter your login password. Go to the directory with the screentshot. Delete it. Close nautilus.

---

### Post by finer recliner on 2007-01-27
> **paydaydaddy said:**
> sorry to be a pain, but I am a noob in the purest sense of the word. An example of script to enter into the terminal would probably save me from turning this into an hours long process. Please?

i dont exactly understand what you're trying to say here. but r4ik's command is pretty simple to follow: sudo will give you full privileges on your system, so if the file wasnt being deleted before because of a permissions error, this will solve it. nautilus is the default file browser on gnome. so when you type sudo nautilus in a terminal, it will open a file browser as root (aka full permissions). please be careful when acting as root, delete the file you want and nothing else, and then exit out. only be root when you have to -- it is the fastest way to screw up your system. 

hope this helps

---

### Post by paydaydaddy on 2007-01-27
> **max.diems said:**
> Type Alt+F2. You will get a window called "Run Application" with a one-line text input. Type "gksudo nautilus". Press enter. If you are asked for a password, enter your login password. Go to the directory with the screentshot. Delete it. Close nautilus.

I did that and still get the message that nautilus has quit unexpectedly. I think nautilus is broke.

---

### Post by r4ik on 2007-01-27
Reinstall nautilus through Synaptic and see if that helps.

---

### Post by paydaydaddy on 2007-01-27
> **r4ik said:**
> Reinstall nautilus through Synaptic and see if that helps.

Once again, I am a total noob. A little help with the uninstall/reinstall would really help. The last time I tried to U&I anything I killed the entire system and ended up reinstalling the OS from scratch, which really isn't to big of a deal since I do not yet keep anything of importance on this computer. But I would like to learn to use Linux to the point that I am no longer so dependant on "Windows and Gates". Do I use the Live CD to do the re-install of nautilus?

---

### Post by Pobega on 2007-01-27
Try this, it should work fine> sudo rm ~/Desktop/screenshot.jpgReplace screenshot.jpg with the name of your screenshot file. I'm not sure what's wrong with Nautilus, but for reinstalling through Synaptic run> gksudo synapticGo to edit in the top, and choose search. Search nautilus in name only (Change description and name to name). You'll see plain "Nautilus" with a green dot to the left of it. Click the dot and choose "Mark for reinstallation". Then click Apply (the green checkmark) and you're done, and hopefully Nautilus is fixed.

---

### Post by paydaydaddy on 2007-01-27
I went through the uninstall/reinstall process for nautilus and restarted the machine. The screen shot popped up, I clicked on it and got the message that nautilus has unexpectedly quit. Now what?

---

### Post by r4ik on 2007-01-27
Try,
Restoring Nautilus as the default

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by max.diems on 2007-01-27
Try switching to Thunar. It is the default XFCE file manager, and very fast. It is worth checking, even if just for this delete.

---

### Post by paydaydaddy on 2007-01-27
> **max.diems said:**
> Try switching to Thunar. It is the default XFCE file manager, and very fast. It is worth checking, even if just for this delete.

That is exactly what I did and it seems to work fine. I will leave thunar as the default file manager as long as it does the job. I did try several times to reinstall nautilus but had no luck. It continued to be broke. I considered downloading the latest version from the GNOME website but figured that I would end up spending several more hours trying to install it and make it work. I am generally cautiously optimistic but Ubuntu is slowly turning me to the dark side of pessimism. I think I'll go work in the yard.

---

### Post by max.diems on 2007-01-27
And as more parts of GNOME break, you gradually switch completely to XFCE.

Or not.

---

### Post by paydaydaddy on 2007-01-27
> **max.diems said:**
> And as more parts of GNOME break, you gradually switch completely to XFCE.

Or not.

If I understand the workings of this Ubuntu thing, Evolution os part of GNOME. Evolution is beginning to act weird. Would a complete switch to XFCE give me a different email client or should I look elswhere, or should I spend several hours of my life that I will never get back trying to fix Evolution?

---

### Post by max.diems on 2007-01-28
If Evolution breaks, use Thunderbird. If you need the calendar, use Sunbird. Both come from Mozilla (so does Firefox, but you probably have that already).

I don't think XFCE has a mail client. I'm not at my Linux system now, and I use webmail.

---

