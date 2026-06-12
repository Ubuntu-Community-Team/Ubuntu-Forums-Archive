---
title: "I can ping a network computer but not access it"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Muad Dib on 2007-11-21
Hi team.  I can connect to the router on my home network.  I am able to access the internet.  I can ping a network computer with shared files and printers, but cannot access the files or printers.  I'm halfway there, but what's the next step?  I need to be able to access the printer on this computer.  Thanks.

---

### Post by dannyboy79 on 2007-11-21
is this other computer a windows computer? Do you know what the Machine name is? if so, try this command to see which shares are available to guests.

smbclient -L WINXP (where WINXP equals the machine name)

when it prompts you for the password, don't enter anything and just hit enter. Does it return any shares or printers?

Next you can try (only if your username's are the same on both machines) try this;

smbclient -L WINXP

this time, enter the password of the machien you're trying to connect to. Any shares shown?

Are you sure you're sharing folders and or a printer frmo the machine you're trying to connect to?

NOTE: in order for this to work, it's possible that ubuntu can't resolve your computer name to the actual ip address so it may fail. if this is the case, then you since you know the ip address, you can add the machine name and the ip address to the hosts file within the /etc/ folder. Read this for local area network name resolving.

[http://ubuntuforums.org/showthread.php?t=391601&highlight=name+resolution](http://ubuntuforums.org/showthread.php?t=391601&highlight=name+resolution)

OR

[http://ubuntuforums.org/showthread.php?t=88206&highlight=name+resolution](http://ubuntuforums.org/showthread.php?t=88206&highlight=name+resolution)

Good luck and if you respond, please answer all my questions so that I can help.

---

### Post by Muad Dib on 2007-11-21
I went through the Network Wizard on both other machines in the network.  The first link was over my head.  I tried the second link and it doesn't seem to be doing anything.  Do I need to reboot?  Any other suggestions.

Here's the screenshot from the smbclient, so let me know what to do if you are able.  I'm such a noob, and this is a struggle.

---

### Post by Muad Dib on 2007-11-21
Something I forgot to mention... The Ubuntu computer is a dual system with an XP/Gutsy install.  When I boot in Windows, the printer is accessible.  So, I know the sharing is turned on.  Why can't Samba see it?

---

### Post by jonandrews on 2007-11-21
I've put a  simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

I'm not sure if it's relevant to your problem, but it might be worth a look


Let me know if it is helpful.

---

### Post by Muad Dib on 2007-11-23
Thanks for the tip.  I'll give 'er a try.

---

### Post by Muad Dib on 2007-11-23
Jon, unfortunately the tip didn't work.  Samba does not pick up the printer.  None of the computers show up either.  Is there some kind of firewall setting I need to tweak on the other network computers.  My anti-virus/spyware program is F-secure.  Thanks for any wisdom.

---

### Post by popch on 2007-11-23
I presume you are using Ubuntu linux (as opposed to Kubuntu or Xubuntu). In that case, you should have a Menu ***Places*** with an entry called ***Network.*** I am guessing at those names as my PC is localized to another language.

If so, click on ***Network.*** That should open a window showing all Windows work groups. Double klicking one of the work groups should show all computers within that work group. Do be patient. Searching the network for work groups and computers takes some time, let's say up to a minute in my home.

Double klicking one of the computers should open yet another window which prompts you for a userid and a password to be used on the computer you double klicked on.

This procedure allows you to use files on Windows computers which are being 'shared'.

For using printers on those computers, you use the Menu System/Setup /Printers (or equivalent). 

I can not give you a step-by-step instructions as I do not use printers shared by Windows. My printers attach directly to the LAN.

---

