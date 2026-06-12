---
title: "Can't empty my trash!"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-03-03
Well I was having issues installing Kibadock and after the install it didn't work so i went to "Computer" and deleted the kiba dock folder. Why? Cuz i'm used to windows =( Anyway, i finally got kibadock to work and when i got to empty the kiba dock crap i deleted earlier OUT of my trash can i get this:

"/home/just...amaru.so.0" cannot be deleted because you do not have permissions to modify its parent folder."

How do i make them gone?

-Justin

---

### Post by harold4 on 2008-03-03
Did you delete it using "sudo?"

---

### Post by oedha on 2008-03-03
sudo apt-get remove kiba-dock
sudo apt-get autoremove

---

### Post by Josh1 on 2008-03-03
> **oedha said:**
> sudo apt-get remove kiba-dock
sudo apt-get autoremove

He said it was in his Garbage Bin.

Have you tried dragging it out, then opening your command line and doing:
```
sudo rm -rf folder
```

Edit: Forgot sudo.

---

### Post by erginemr on 2008-03-03
You should go into your hidden ".Trash" folder and use sudo to delete all files in there:

1. First open a terminal.

2. Change into the .Trash folder:
```
cd ~/.Trash
```
where tilda(~) stands for your home folder.

3. First, make sure that you are in the trash folder:
```
pwd
```
This is [COLOR="Red"]**crucial**[/COLOR]! Otherwise, the command below will delete[COLOR="Red"] **everything**[/COLOR] inside the whatever directory you are in, which may render your system unusable.

4. Use sudo to delete all files in your trash can:
```
sudo rm -r *
```

5. If you want to play safe, you can use
```
sudo rm -ri *
```
instead, which will require your permission at the deletion of each file.

---

### Post by Crafty Kisses on 2008-03-03
-Do Alt+F2
-Type gksudo nautilus and enter your password
-You should now be in your root folder
-Navigate to your home folder and enter the hidden folder .Trash (To view hidden files and folders do Ctrl+H)
-Delete the files
-Go back to the Root folder
-There is a .Trash in there as well if it doesn't show try Ctrl+H again
-Now delete the files from there as well
-They should be gone for good at this point

---

### Post by erginemr on 2008-03-03
Or simply opening a terminal screen and writing:
```
sudo rm -r ~/.Trash/*
```
will do.

Again the ending part ".../*" is crucial. Otherwise, you will end up deleting the trash folder itself.

---

