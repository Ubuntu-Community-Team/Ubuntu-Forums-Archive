---
title: "[SOLVED] A button like F5 to keep a running log?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-04-14
In Windows I can have a text file with the *.txt extension (which just about everything can open).
Whilst writing in that file by pressing F5 a line with the date and time is generated.
This is most valuable for taking notes: talking to people on phone. Press F5 and jot down what they say -- so it becomes a log of what happened and when, to the minute.
How can I do this in Ubuntu?
Any replies gratefully received.
Regards
John

---

### Post by hyperair on 2008-04-14
Go to Edit->Preferences (in text editor). Go to the last tab "Plugins". Make sure "Insert Date and Time" is checked. Then go to your Edit->Insert Date and Time menu item. Don't click it. Just leave your cursor over it, and press "F5". F5 should appear on the right side of that menu item. Now when you press F5, it will insert a date. To make it automatically insert a specified format instead of prompting you every time, go back to Plugins and click adjust the preferences for that plugin.

---

### Post by Andavane on 2008-04-14
> **hyperair said:**
> Go to Edit->Preferences (in text editor). Go to the last tab "Plugins". Make sure "Insert Date and Time" is checked. Then go to your Edit->Insert Date and Time menu item. Don't click it. Just leave your cursor over it, and press "F5". F5 should appear on the right side of that menu item. Now when you press F5, it will insert a date. To make it automatically insert a specified format instead of prompting you every time, go back to Plugins and click adjust the preferences for that plugin.
I take it we are in the "gedit" program?
Yes "Insert Date and Time" is cheked, and I see it under the same heading in the edit menu.
However, when I leave my cursor over it and press "F5" nothing happens as yet...

Regards

John

---

### Post by hyperair on 2008-04-14
Yes we're in the gedit program. Ah first of all you have to enable editable menu shortcut keys.

Go to System->Preferences->Appearance. Then navigate to the "Interface" tab. Look for a checkbox "Editable menu shortcut keys". Make sure it's checked. Then try again.

---

### Post by Andavane on 2008-04-14
> **hyperair said:**
> Yes we're in the gedit program. Ah first of all you have to enable editable menu shortcut keys.

Go to System->Preferences->Appearance. Then navigate to the "Interface" tab. Look for a checkbox "Editable menu shortcut keys". Make sure it's checked. Then try again.

"I give Thee thanks, Grim Reaper, for
Thou hast spoken well, and wise."

Now before I let thy scythe fall on this thread by marking it as "solved", may I perchance squeeze in another question?

When I double-click on the gedit file, it brings up a menu which has four options on it and I have to click "display".

Could you, Great Leveller, inform me how to put a short opening form here? ;)

Kind regards

John

---

### Post by hyperair on 2008-04-14
Could you screenshot that please? I was not aware that there were options when you double clicked on a text file.

---

### Post by mister_pink on 2008-04-14
The text file must be marked as executable when it shouldn't be. Right click, properties, permissions and untick the executing as a program option. You can turn this behaviour off entirely by opening a nautilus window, then edit, preferences, behaviour, executing text files section. 

On another note, I'm always amazed that I learn something new every day, I had no idea you could assign shortcuts like that!

---

### Post by Andavane on 2008-04-14
> **hyperair said:**
> Could you screenshot that please? I was not aware that there were options when you double clicked on a text file.

[ATTACH]65990[/ATTACH]

---

### Post by Andavane on 2008-04-14
> **mister_pink said:**
> The text file must be marked as executable when it shouldn't be. Right click, properties, permissions and untick the executing as a program option. You can turn this behaviour off entirely by opening a nautilus window, then edit, preferences, behaviour, executing text files section. 

On another note, I'm always amazed that I learn something new every day, I had no idea you could assign shortcuts like that!
Yes mister_pink it's marked as executable and you can't untick it.

[ATTACH]65991[/ATTACH]

---

### Post by hyperair on 2008-04-14
Uncheck the "executable" box.

---

### Post by mister_pink on 2008-04-14
Its group is root, is this intended? If not, go to a terminal and cd to the directory where the file is, then
sudo chown $USER:$USER filename
chmod a-x filename

Still, you ought to be able to just untick it since you are the owner.

---

### Post by Andavane on 2008-04-15
> **hyperair said:**
> Uncheck the "executable" box.
I can't.
If you look at the screenshot, you will see an orange minus sign next to execute.
If I click there, a tick appears in the box for a brief second and then vanishes again.

---

### Post by hyperair on 2008-04-15
From the screenshot I see that you're the owner of the file, but the group that owns it is "root". Change that to "andavane" and then you'll be able to uncheck the checkbox.

---

### Post by Andavane on 2008-04-15
> **mister_pink said:**
> Its group is root, is this intended? If not, go to a terminal and cd to the directory where the file is, then
sudo chown $USER:$USER filename
chmod a-x filename

Still, you ought to be able to just untick it since you are the owner.
I didn't have any intentions about root, it is just there.
As I am still rather new to use this, I will need to try to study about the command given above, so I understand what I am doing.
And I will need to try to find out in which directory the file is stored.
At nearly 60 years old, these are a lot of tricks for this dog to learn, but I want to keep on trying. It is rather a learning curve!
Sometimes unfortunately things go blank, but they usually come back in a moment of clarity.
Regards
John
PS: I generated the file by right clicking and selecting "create document", then selecting "empty file" at the bottom of the menu.

---

### Post by mister_pink on 2008-04-15
Its strange that the group was created as root then, not sure how it ended up like that. 

Basically the first command changes the owner and group owner of the file to you ($USER expands to your username). 
The second one changes the file permissions, for (a)ll minus e(x)ecute permissions. 

Have a look at these sites: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by Andavane on 2008-04-16
> **hyperair said:**
> From the screenshot I see that you're the owner of the file, but the group that owns it is "root". Change that to "andavane" and then you'll be able to uncheck the checkbox.
Thank you.
But when I try to do that it tell me that I don't have permission.
[ATTACH]66146[/ATTACH].

To pick up what mister_pink said: It is indeed odd that the file is set to root. I tested the equivalent on my laptop, and it is fully executable.
Regards
John
NB; am studying the suggested links. One of the tutorials gives lists and charts which are totally baffling to me.

---

### Post by Andavane on 2008-04-17
Thank you gents, I've looked at the this again.
Remembering that the file I was looking at was on another drive, I looked at the drive on which linux is installed. In the linux drive you can tick the box as executable if you wish, but it opens normally anyway. It only happens, it seems, when I open it on the other drive, where windows is.
When I went edit in gedit and held the cursor over insert time and date and pressed F5, the letters didn't appear to the right, it made a noise instead.
Nonetheless, when I press F5 in text now, time and date appears in the format I want.
Thanks again, and marking this thread now as "solved".
Kind regards and thanks
John

---

### Post by mister_pink on 2008-04-18
Ahh, that explains it - your windows drive will probably be NTFS formatted, and this doesnt offer any way of storing file permission information for ubuntu, so you can only set permissions for the entire drive.

---

### Post by Andavane on 2008-04-19
> **mister_pink said:**
> Ahh, that explains it - your windows drive will probably be NTFS formatted, and this doesnt offer any way of storing file permission information for ubuntu, so you can only set permissions for the entire drive.
errr... I don't think it totally explains it as the file is stored in a separate FAT32 partition on the first drive which also houses windows in the "C" drive.
Regards
John

---

### Post by hyperair on 2008-04-19
Still explains it. FAT16, FAT32, and NTFS filesystems don't support Unix permissions.

---

### Post by Andavane on 2008-04-20
> **hyperair said:**
> Still explains it. FAT16, FAT32, and NTFS filesystems don't support Unix permissions.
Yes it does indeed explain it.
I will remember that - and thanks.

---

