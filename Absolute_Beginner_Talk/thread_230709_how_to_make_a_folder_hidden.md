---
title: "how to make a folder hidden?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2006-08-06
any clue??
please help, there is some material i wouldn't like my gf to see :twisted:

---

### Post by meng on 2006-08-06
Simplest way:

Say your folder is named gayp0rn.
Rename it to .gayp0rn, ie:

mv gayp0rn .gayp0rn

---

### Post by cheway on 2006-08-06
You'll have to tell us what it is first.... [-(  ;) 

Put a fullstop . in front of the file/folder name. You can then hide/unhide folders with Ctrl+H.

---

### Post by moma on 2006-08-06
Encfs (Encrypted File System) is an excellent tool.  You can very easily encrypt a folder with it.

o--> [http://forums.osdir.com/forum/viewtopic.php?t=532]("http://forums.osdir.com/forum/viewtopic.php?t=532")

Of course you can create an encryped directory under your $HOME folder.
----------------------------------------------------------------------

You can easily make it more usable.  

1) Create a tiny shell-script that uses zenity-GUI to ask a password. Save it to $HOME/askpass.sh
$ cat $HOME/askpass.sh
```
#!/bin/bash
echo $(zenity --title "Encrypted folder" --entry --text "Enter your password:")
```

Make the script executable
$ chmod +x $HOME/askpass.sh 

And do:
$ [COLOR="Green"]sudo encfs /home/.crypt /home/crypt --extpass=$HOME/askpass.sh[/COLOR]

---

### Post by bluntu on 2006-08-06
I have used TrueCrypt on Windows and it's an excellent program! Haven't tried it on Linux yet but do check it out because it's OPENSOURCE and is available for LINUX.

Anyone that carries a Laptop around in public better have TrueCrypt installed because if your Laptop got stolen the data will be useless to the thieve. Visit here: [http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm)  and scroll down and look for Episode #41 and download the audio of Steve Gibson talking about TrueCrypt (very informative). You can find the software at: [http://www.truecrypt.org](http://www.truecrypt.org)

Also, visit YouTube.com and search for TrueCrypt you will find a walkthrough that shows you how to set it up (For Windows unfortunately).

Good luck.

---

### Post by kebes on 2006-08-06
Another simple option is to create a new user and put the files in question in that user's home directory. When you want to use/view the files, you switch to that user and do what you want. When you're done you log out. Assuming other people don't have your root password they won't be able to see the files (without doing something fancy like booting from a LiveCD).

You can name the new user something innocent sounding like "test" or "admin".

---

### Post by orb9220 on 2006-08-06
I have been using truecrypt works great. No GUI tho there working on it.

I considerate to be one of if not the strongest encryption package.

[http://www.truecrypt.org/](http://www.truecrypt.org/)  and the have a linux section in their forums.

---

### Post by XDevHald on 2006-08-06
> Quote by: [B]meng

[/B] 			 		 		 		 		Simplest way:

Say your folder is named gayp0rn.
Rename it to .gayp0rn, ie:

mv gayp0rn .gayp0rn



Who said anything about gayporn? we have little kids viewing these forums and don't need these words being passed around.

---

### Post by catlett on 2006-08-06
Just to clarify. When you name a file/folder, if you put a . (period) before the letters it will be hidden. 
There are many hidden files/folders on your system already. Go to Places<Home Folder. When nautilus opens up go to "View". Then check off "show hidden folders". This will allow you to view hidden files/folders. You will then see all the . files/folders in your home.
This method only hides the file/folder from the file browser. It doesn't encrypt it. The third party apps already mentioned are what you will need if you want to encrypt.

---

