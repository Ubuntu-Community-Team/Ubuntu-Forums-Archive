---
title: "Installing software"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Terrigal on 2008-03-28
Problem
I have downloaded Google desktop for linux to my desktop.                                                                   When I open the package I am asked to grant admin rights to install the software and asked for my Password
i get the message--
"Failed to run gdebi-gtk '--non-interactive' '/home//Desktop/google-desktop-linux_current_i386.deb' as user root.
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Where can I go from here?  Should I try inserting the CD and reinstall. Can I damage things?

---

### Post by Joeb454 on 2008-03-28
Try opening a terminal, and using the following:
```
cd ~/Desktop
sudo dpkg -i ./google-desktop-linux_current_i386.deb

```

Does that give the same error?

---

### Post by kool_kat_os on 2008-03-28
> **Joeb454 said:**
> Try opening a terminal, and using the following:
```
cd ~/Desktop
sudo dpkg -i ./google-desktop-linux_current_i386.deb

```

Does that give the same error?

is the  "~" part of ~/Desktop the same as ./Desktop ?

---

### Post by Golem XIV on 2008-03-28
You might try 
```
gksu /usr/bin/x-terminal-emulator
```
and see if it works better.

On a side note, why Google Desktop?  From what I can see, Tracker can do the same job.

---

### Post by Joeb454 on 2008-03-28
**kool_kat_os** ~/ in Linux means /home/<user>/

So for me ~/ is the same as typing /home/joe/

And as the default terminal opens in your /home directory (which Desktop is a folder within ~/) it is exactly the same in this case, as running ./Desktop.

I hope that made sense :)

---

### Post by Terrigal on 2008-03-28
Please 'What or where do I find Terminal?

---

### Post by fatality_uk on 2008-03-28
Go into the Applictions menu, then into Accessories and then select terminal ;)

---

### Post by Terrigal on 2008-03-28
Copied and posted to Terminal with no result???

---

### Post by Joeb454 on 2008-03-28
Did you hit enter after you pasted it? I know it sounds stupid...but there should at least be some feedback.

Also you should post the code above 1 line at a time :)

---

### Post by Terrigal on 2008-03-28
Yes I did hit enter. It then asked for sudu password which it would not accept?
Another Question  With this chat do you have to hit refresh to get replies?

---

### Post by Joeb454 on 2008-03-28
Yes, because it's a standard HTTP webpage, you'll have to hit refresh to see replies (or F5, which does the same thing :))

And the password does get accepted, provided you type it correctly with no spelling mistakes. It just won't show that you're entering any characters. It's the way *nix has always been :) Try it and see :)

---

### Post by SunnyRabbiera on 2008-03-28
actually we sort of have an alternative to google desktop called the deskbar, its pre installed with your system.
go to thew top or bottom and right click "add to panel"
and add the deskbar applet, it has both desktop search and world wide web search.
you may want to play around with its preferences.

---

