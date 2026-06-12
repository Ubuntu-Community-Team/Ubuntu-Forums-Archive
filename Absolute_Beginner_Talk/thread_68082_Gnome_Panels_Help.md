---
title: "Gnome Panels Help"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by hiperactive on 2005-09-22
Hello

I was costumising my panels in Gnome, I added a new panel to experiment there and everything went fine (it's incredible how similar to windows it could look) but when I was adding another item to new panel, suddenly the computer computer froze and I could only move the mouse pointer but slowly, the keyboard was not responding and one of the items I added to the panel (system monitor?) showed that CPU was completely busy. Since alt+ctrl+bkspace or alt+ctrl+f1 didnt work, I had to reboot the computer manually. Now everytime I log in with that account, as soon as that panel  is shown the computer hangs again. I guess there must be a way of deleting that panel via console but I dont know how. 

Can someone help me please? Thanks in advance.

 :cool:

---

### Post by Perfect Storm on 2005-09-22
Which version of Ubuntu do you use? Could be a bug to report if it's breezy.
See if 'killall gnome-panel' makes any change.
May I ask what you add to the panel?

---

### Post by hiperactive on 2005-09-22
[QUOTE=Artificial Intelligence]Which version of Ubuntu do you use? Could be a bug to report if it's breezy.
See if 'killall gnome-panel' makes any change.
May I ask what you add to the panel?[/QUOTE]

Yes, I am using Breezy but I could not say what exactly was the bug since I had about 10 items running in this new panel (I was experimenting) when this error came up, I was about to the add the windows list to the panel and I could just click on it. But The strangest item which was never shown was the modem monitor maybe it was the cause.

Anyway I think I found a way to solve this:
Copy the folder /etc/gconf/gconf.xml.defaults/apps/panel/default_setup (default for new user) to /home/user/.gconf/apps/panel/profiles/default but I cant do that using nautilus and I think I am not sure how to do it using the command line. Nautilus doesnt even let me see the folder /.conf telling me I am not authorized.

I have two other questions: 
-Is there a way to give permissions in Nautilus? I want to see and write in any folder. Well I dont think I could so I guess I should have the owner privilegies of my whole harddisk, how can I do that?

-How can I access to the /. (hidden?) folders in console mode, if I do cd /.folder it tells me the directory doesnt exist.

bye for now

EDIT: ok, found the command: gksudo nautilus but I stil cant get access to one specific folder (root/.gconf).

---

