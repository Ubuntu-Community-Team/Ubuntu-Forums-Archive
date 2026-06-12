---
title: "Thunderbird messages/settings transfer"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-10-07
Hello!
How can i transfer all my emails and settings from my windows Thunderbird to my Ubuntu Thunderbird?

---

### Post by PPAAUULL on 2006-10-07
I Think that there is an export function and an import function. That should do what you want.

---

### Post by elettronicha on 2006-10-07
> To save your email, you need to find the data files that contain your email messages in Thunderbird. There is a set of files in the following directory in Windows XP and Windows 2000:
C:\Documents and Settings\username\Application  Data\Thunderbird\Profiles\randomletters\
In Windows 98 and Windows ME, the directory is different:
C:\Windows\Application Data\Mozilla Thunderbird\Profiles\randomletters\
In the above examples, substitute your Windows username for the "username" in the path (if you did not set up user accounts in Windows, choose the Administrator folder here), and the "randomletters" are going to be a random series of letters that uniquely identifies each installation of Thunderbird. The Application Data folder may be hidden. To unhide it, go to the Tools menu and click on Folder Options, then click on the View tab, then on the Show Hidden Files And Folders option. Click on OK to finish.
The files you need to backup are called Inbox and Sent, and they're in the Mail directory. So double-click on Mail, then add the Inbox file and the Sent files to your backup. If you had any draft email messages, copy over the Drafts file as well. That's all of the data you have to save, so you can write your CD and exit Thunderbird.

> For email, the import process is a little more difficult. Start by clicking on your Home icon, either on your desktop or in the quicklaunch area near the top (on GNOME) or bottom (on KDE) of your screen. If you're using GNOME, the Nautilus file manager will come up. Go to the View menu and select Show Hidden Files. Now find the folder called .thunderbird and open it. Inside of that folder is another folder with a bunch of random characters; open it. From there, open the Mail folder. There you should see yet another folder, but this one will have your email account as its title. Open that, then open the CD icon on your desktop. You should now have two open windows -- the one you just navigated to, and your backup CD. Drag and drop your Inbox and Sent files from the CD to the first window. Once they are copied, close the CD window, then select the Inbox and Sent files that you just copied. Right-click them, select Properties from the popup dialogue, and change their file permissions so that they may be written to (files that were stored on a CD will, by default, be unwritable when you copy them to your hard drive).



[http://www.softwareinreview.com/cms/content/view/29/](http://www.softwareinreview.com/cms/content/view/29/)

---

### Post by Blagomir on 2006-10-07
Thanks!

---

### Post by elettronicha on 2006-10-07
Not at all, let me know if it worked! ;)

---

### Post by msak007 on 2006-10-07
If I'm not mistaken, you can copy the entire profile folder (the random letters and numbers), and place it in /home/<username>/.thunderbird/ - this will load all the user settings, email, and extensions as well. But if you have any Windows only extensions, it may hang the application when starting.

---

### Post by TheEHMan on 2006-10-13
> **msak007 said:**
> If I'm not mistaken, you can copy the entire profile folder (the random letters and numbers), and place it in /home/<username>/.thunderbird/ - this will load all the user settings, email, and extensions as well. But if you have any Windows only extensions, it may hang the application when starting.

That turned out to be the easiest way to do it.  Copy the PROFILE folder to /home/<username>/.mozilla-thunderbird/ - once there you can rename it to the default profile folder already there or edit the profile path line of profiles.ini to reflect the name of your profile folder.

---

### Post by aysiu on 2006-10-13
> **msak007 said:**
> If I'm not mistaken, you can copy the entire profile folder (the random letters and numbers), and place it in /home/<username>/.thunderbird/ - this will load all the user settings, email, and extensions as well. But if you have any Windows only extensions, it may hang the application when starting.
You are not mistaken.

---

### Post by msak007 on 2006-10-14
> **TheEHMan said:**
> That turned out to be the easiest way to do it.  Copy the PROFILE folder to /home/<username>/.mozilla-thunderbird/ - once there you can rename it to the default profile folder already there or edit the profile path line of profiles.ini to reflect the name of your profile folder.

You really don't have to rename anything or mess with any .ini files. You can just run the Profile Manager, create a profile name, and point it to the profile folder you want to use. Here's a quote from the [Thunderbird page on profiles]("http://www.mozilla.org/support/thunderbird/profile"):

> On Linux, start Thunderbird with the the   -profilemanager switch, e.g. ./thunderbird -profilemanager (this assumes that you're in the Thunderbird directory).

I used to do this when I was using Thunderbird and it's the easiest way to manage profiles so you don't have to mess with any configuration files.

---

