---
title: "do not own folder"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by hoff14 on 2008-03-06
I am very new to linux. I am trying to move some file into a folder and I get the following message." Permissions cannot not be modified because you do not own the folder" How can I get ownership of my folder, please help!

---

### Post by lswest on 2008-03-06
first off, what folder are you trying to move a file to?  if it's owned by root then the best thing to do would be use the command ```
sudo mv [file] [destination]
``` after which it will ask for a password, enter your password (it won't show any input, just type and hit enter) and then it'll move it to the folder.  Changing the ownership of system folders is bad, as it prevents the system from booting/working correctly.

---

### Post by prshah on 2008-03-06
Generally not a good idea to muck around with file/folder ownership/permissions. What files are you trying to move where?

Anyway to gain ownership of files / folders, first try "chown -R yourname file_or_foldername", and if it fails (most likely it SHOULD), repeat the same command with a "sudo" in front of it.

Once again, not a good idea unless you know what you are doing, if you have any doubts, pls answer the first question above.

Cheers,
PRShah

---

### Post by hoff14 on 2008-03-06
I am trying to move 4 dll into wine/drive_c/windows/system32. I need to move them so my esword will show the text.

---

### Post by lswest on 2008-03-06
well do this then:
```
cd [path to dll files]
sudo mv *.dll /home/<username>/.wine/drive_c/windows/system32/
```
where the path to the dll files will be something like /home/<username>/[where you have them saved] and the second command moves all .dll files to windows/system32.  However, if you're copying this from a windows partition, replace mv with cp to COPY the files there.  hope that helps

---

### Post by stchman on 2008-03-06
> **hoff14 said:**
> I am very new to linux. I am trying to move some file into a folder and I get the following message." Permissions cannot not be modified because you do not own the folder" How can I get ownership of my folder, please help!

I agree with poster #2.  The only folder you should own on the / drive is your home folder.  Everything else is and should be owned by root.  Having root own everything is one of Linux's big security features.

If you need to move some files into a root owned folder then use sudo.

example

sudo mv <file you  wish to move> <location of where you want files to go>

---

### Post by hoff14 on 2008-03-06
I am sorry put I have been using windows wave to long and I need to know how to make the path with the right syntax right. My dll's are in My Documents/e-sword. It is going into the wine/c/windows/system32.I really thank you for all your help and patients. It is great to have people who can help you!

---

### Post by lswest on 2008-03-06
is this "My Documents" the one on your windows drive/partition, or on your Linux one?  if it's the linux one: ~/Documents/E-Sword/ (the ~ is a shortcut for your home folder, meaning it's there instead of /home/<username>/)
(note: if the folder is actually My Documents, you will need to replace Documents with "My\ Documents" minus the quotes, where the "\" tells Linux that the space is in the filename)

so the code would be ```
cd ~/Documents/e-sword/
sudo mv *.dll ~/.wine/drive_c/windows/system32/
```

---

### Post by hoff14 on 2008-03-06
Hi all,
It is tell me is not a directory: No such file find

---

### Post by wolfen69 on 2008-03-06
```
gksudo nautilus
```
then physically move them. copy and paste/drag and drop.

---

### Post by hoff14 on 2008-03-07
Do I need to put anything else with that line?

---

### Post by aysiu on 2008-03-07
If it's in ~/.wine, then you should already own the folder.

Don't use *sudo* to move it in this case. You really should change ownership of the folder to yourself.

---

### Post by hoff14 on 2008-03-07
How do you change the ownership? Also I am very new to Lunix and the propject I am working on is very important to my work I can not afford to put wrong code or anything. This will make me go back to using windows. I do not want to do that!

---

### Post by aysiu on 2008-03-07
> **hoff14 said:**
> How do you change the ownership? Also I am very new to Lunix and the propject I am working on is very important to my work I can not afford to put wrong code or anything. This will make me go back to using windows. I do not want to do that!
I'm not going to give you the wrong code, **but** you should always have backups of all your important data. This is true for Linux, Windows, Mac--whatever operating system you use. Power failures, power outages at inappropriate times, accidental deletions, etc. are all a part of life.

The command you want is ```
sudo chown -R *username:username* /home/*username*/.wine
``` where *username* is your actual username. So if your actual username were hoff14, the command would be ```
sudo chown -R hoff14:hoff14 /home/hoff14/.wine
```

---

### Post by david_kt on 2008-03-10
If you follow below instruction carefully:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

you should have a fully running esword.

If you have problem copying the dll, it might be you try to copy to the wrong place. The right place is:

```
~/.wine_Esword/drive_c/windows/system32
```

You could use nautilus to go to that folder if you are not familiar with command line.

DK

---

