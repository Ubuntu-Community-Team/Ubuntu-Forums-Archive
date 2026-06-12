---
title: "How do I get a command line up?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by archolman on 2007-06-14
**How do I get a command line up? I tried a *terminal*, but no joy. And, how do I set my*** **root** *[B]password?
6.06LST on a PentiumIII with enough RAM, soon to be joined by 7[/B]**.04 & Xubuntu6.06LST(hehehehe)**

---

### Post by Anonii on 2007-06-14
Greetings there,

check this guide out for the first part of your question: [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

You can, now, change your root password using this command: sudo passwd root

EDIT: Aw ****, I forgot that there is no root account in Ubuntu. Disregard the previous sentence.

---

### Post by Inxsible on 2007-06-14
> **archolman said:**
> **How do I get a command line up? I tried a *terminal*, but no joy. And, how do I set my*** **root** ***password?**
**6.06LST on a PentiumIII with enough RAM, soon to be joined by 7****.04 & Xubuntu6.06LST(hehehehe)**
Terminal is actually a GUI version, even tho you type commands in, you are still within the GUI framework.
 
I think, Ctrl + Alt + F2 will get you to a Command Line.

---

### Post by dannyboy79 on 2007-06-14
all of the above info is spot on except for the last bit directly above. I'll explain,  if you possibly meant that you wanted to get to a Virtual terminal console ( i doubt but thought I'd still inform you), than you do that by hitting ctrl-alt-F1, which will take you to a NON-GUI (meaning no X-server) Virtual terminal consoles which in ubuntu goes by the name of "getty". You can login and then do whatever you want there, but this is all thru the command line (like DOS) and you can always get back to your "getty" that's running your X-server by hitting ctrl-alt-F7. If you do a command to show you all your processes, you'll see that you actually have 7 of these getty's total, but only 6 will show up because the 7th is always for your x-server, well I think it actually runs gdm, but after you login using gdm, it launches your X-server.

If you just want a little dialog box to run simple command within a terminal but don't want to have to open a terminal first, use alt-f2 (i am guessing that's what the previous poster meant to write but I can't be sure as I can't read minds and who am I to speculate what other people mnight have meant! he he), that will open a dialog box which is wher eyou can enter commands.

---

### Post by bapoumba on 2007-06-14
Please read 
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") regarding the use of sudo/gksudo to run applications as root. There are very little cases where you actually need to enable a root account (did not here).

---

### Post by dannyboy79 on 2007-06-14
> **Anonii said:**
> Greetings there,

check this guide out for the first part of your question: [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

You can, now, change your root password using this command: sudo passwd root

EDIT: Aw ****, I forgot that there is no root account in Ubuntu. Disregard the previous sentence.

there's a root account in ubuntu! I use it all the time, what you're thinking of is that it's not setup for your to login as root by default. also, root doesn't have a password by default. so your command
sudo passwd root
is correct to set the root password only IF you also want to enable logging in as root. BUT as the above posteer mentions, you won't ever neeed to login as root, UNLESS you need to delete your own account or similar. You can always log in as yourself and switch user to root using many different commands but I accomplish with this command:
sudo -i
you'll need to do this on some commands that dont' work with sudo.

---

