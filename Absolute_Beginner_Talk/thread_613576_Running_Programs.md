---
title: "Running Programs?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by scriptsales on 2007-11-15
Two Questions really, one is concerning Terminal sessions and the other is general advice.

When I dropped into the terminal I needed to create a couple of directories and do some other stuff. Is there any way to not have to type sudo in front of every command? (I know its only 4 letters and a space but I am a lazy, lazy man!)

Like is there a way to run a terminal session and say "OK I am the administrator, please don’t bother asking me again this session"?

Secondly, showing my windows heritage here, I recently installed some programs using Synaptic, went fine, no problems reported but I can’t find them! I am used to newly installed programs either being added to a menu under start -> all programs (so expected them to appear somewhere under the applications menu) or having a nice little shortcut icon on the desktop. 

The main program I installed was Thunderbird, it installed OK, I can find the program directory but I can’t for the life of me figure out how to actually run the program (nor even what constitutes the program, no .exe file so is it the shell script or the bin file that you have to make run?)

Cheers
Andy

---

### Post by paul.matthijsse on 2007-11-15
1. type "sudo su -" in a terminal
EDIT. Don't forget to type "exit" when you're done, as an open root account is a security risk.

2. Thunderbird should be under Apps - Internet. If not, some people suggest to log out from X (no reboot) and log in again. If not, type "thunderbird" in a terminal. If that doesn't work, type "sudo updatedb" in a terminal, let it run for a minute or so, and type "locate thunderbird". On my box it is in /usr/bin.

---

### Post by smartbei on 2007-11-15
Note that you shouldn't usually have to use sudo to make directories - That is, you shouldn't usualy be making a lot of directories in a folder owned by root. Where are you trying to make them? If they are all in a single non-system folder, you should chown them to you:

```

chown -R <yourusername> <folder>

```

Then you won't need to use sudo.

---

### Post by scriptsales on 2007-11-15
Thanks for the advice, I'll take a look when I get home. I didnt re-boot or log off after the install so maybe it will turn up again when I log back in.

One more thing, I tried to install Adobe Reader, following the download of the .tar package I simply tried to extract the contents (Using the GUI, not the command line) and was told the directory /usr/lib/Adobe7.0/Adobe/Reader didnt exist (Hence the reason for creating several directories) I also got an error message about permissions so I am guessing that using the GUI to extract files runs them with normal user privileges and that to extract packages you would need root privileges so is there any way to run GUI applications (from Computer or My Computer, cant remember what it's called) as root? I know Ubuntu is not Windows but is there no equivalent of right click -> run as?

Cheers 
Andy

---

### Post by hyper_ch on 2007-11-15
Adobe Reader is in some repos... either medibuntu or canonical commercial (which are now called differently). So you'll need to add those repos and you can install it from synaptic...

But then, what do you need AR for? Evince handles PDFs just fine and is way more light-weight.

Regarding root:
Why are you so obsessed getting root right? There's a pretty good reason you normally don't have root rights. Are you sure you need it?

---

### Post by CatKiller on 2007-11-15
**sudo -s** will let you be root for a while. **exit** when you're done. It's not like you need to type in the password every time, and if you're taking proper security precautions you'll almost never need to use sudo anyway. You can do whatever you want in your Home folder, for example.

Sometimes the menu needs updating to reload the new entries. **killall gnome-panel** will do that for you without you having to log out. To run programs without a menu entry, you generally just need to type the name of the program. For example, to run Thunderbird, you could type **thunderbird** into a terminal.

---

