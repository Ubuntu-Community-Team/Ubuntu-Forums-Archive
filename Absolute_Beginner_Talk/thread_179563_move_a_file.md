---
title: "move a file"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-05-20
:) Hallo

I'm trying to move a file (realplayergold10.bin) from the desktop to usr/local; and I bump into a message which goes more or less like this: you don't have the permission! :confused: 

Is there any way out? When I download sth, it goes straight to the desktop, and I can't change the destination before the download. ](*,) 

Thanks

---

### Post by meng on 2006-05-20
Use sudo mv, you probably need superuser privileges.

---

### Post by jorn on 2006-05-20
Or type into terminal : gksudo nautilus
if you want a grafical one. But be careful, you have the permission to do everything.

---

### Post by Sef on 2006-05-20
> When I download sth, it goes straight to the desktop, and I can't change the destination before the download.

What browser are you using?

---

### Post by Ecthelion on 2006-05-20
It's not normal that you can't the files on your desktop... Your desktop is in your home folder, and you should have (more or less) all permissions.
Have you checked the permissions of your desktop?
What are they?

---

### Post by mostwanted on 2006-05-20
[QUOTE=Ecthelion]It's not normal that you can't the files on your desktop... Your desktop is in your home folder, and you should have (more or less) all permissions.
Have you checked the permissions of your desktop?
What are they?[/QUOTE]

He's moving them to /usr/local which is owned by root. This is completely normal.

**To the original poster:** Each user only has write permissions to his own home folder and its subfolders, but it's possible to ascertain super-user (or root) privileges using the *sudo* command.

You can start up the nautilus file manager with super user privileges like this:

```
sudo nautilus
```

It will ask you for your password (won't write stars or anything, but it does record what you write).

---

### Post by Ecthelion on 2006-05-20
[QUOTE=mostwanted]He's moving them to /usr/local which is owned by root. This is completely normal.[/QUOTE]

Right. Didn't thinked of that...

---

### Post by meng on 2006-05-20
Now the next question is whether or not it's advisable to move that file to /usr/local at all. Of course, you're free (as in speech) to do so, but isn't that the install program for realplayer? So it really doesn't matter which folder you run it in, right? You may want to install stuff _into_ /usr/local/RealPlayer (or whatever) but IIRC it will prompt you for that.

---

### Post by mostwanted on 2006-05-20
Install realplayer from the repositories instead. It will pop up a dialog asking you where the realplayer binary file (the .bin you have on your desktop) is located and install it for you. Much easier.

Remember to enable all repositories.

---

### Post by helphope on 2006-05-20
Tnaks to everybody for the answers:) :) 


[QUOTE=mostwanted]Install realplayer from the repositories instead. It will pop up a dialog asking you where the realplayer binary file (the .bin you have on your desktop) is located and install it for you. Much easier.
Remember to enable all repositories.[/QUOTE]

I dit it and then "error while loading shared libraries: libstdstdc++.so.5: cannot open shared object file. No such file or directory.](*,) 


The browser I use for my download isOpera 9 beta

Thanks again

---

### Post by mostwanted on 2006-05-20
[QUOTE=helphope]Tnaks to everybody for the answers:) :) 




I dit it and then "error while loading shared libraries: libstdstdc++.so.5: cannot open shared object file. No such file or directory.](*,) 


The browser I use for my download isOpera 9 beta

Thanks again[/QUOTE]

Try installing libstdc++ 5 - it's in the repos.

---

### Post by catlett on 2006-05-20
Did you use apt-get to install? If so try aptitude. It will install any dependencies if it has acces to them. If you're not used to aptitude, it is just like using apt-get. Just replace apt-get with aptitude in the command. Hopefully that library is in the repo.

---

### Post by helphope on 2006-05-20
:( :( 

Thanks to everbody. I tried everything (also installed the  libstdc++ 5  in the repos) but to no point. I managed to launch the installer and a set-up assistant helped me throguh configuring RealPlayer. Everything seemed OK, but when I click on the icon, ... nothing happens.

I'll try again from the very beginning tomorrow, hope so.

GOod night

---

### Post by catlett on 2006-05-20
> **helphope]:) Hallo

I'm trying to move a file (realplayergold10.bin) from the desktop to usr/local said:**
> (*,) 

Thanks
Just a quick note about Firefox downloads. Hit on "edit" then "preferences" then "downloads". In the "download folder" section check off the box "ask me where to save every file". This way when you download from firefox it will give a prompt asking you where you want the download and you can put it wherever you want.

---

### Post by helphope on 2006-05-22
As far as I could understand, I could move the file into /usr/local directory with the following command:
1) on the terminal line I move on the Desktop directory (cause the file which has to be moved lies in this directory)
2) sudo mv file /usr/local/whatever

Is this correct?

I tried as mostwanted suggested: sudo nautilus, ... nothing happened. No permission given.

As to Firefox, I cannot choose a root directory as final destination for a download. It pushes me back:confused:

---

### Post by Ecthelion on 2006-05-22
I think that should work but I sure this works:

```
sudo mv /**file_path** /**new_file_path**
```

EDIT: that's what you do: 'caus you first go in the dir in wich the file is. When you type just sudo mv file /new location then it's correct if the file is in the dir you are currently in.
LOL lot's of words to say you'r right

---

### Post by Ecthelion on 2006-05-22
[QUOTE=helphope]
As to Firefox, I cannot choose a root directory as final destination for a download. It pushes me back:confused:[/QUOTE]

I think you could but only if you start firefox with
```
sudo mozilla-firefox
```
and that's not something I would advice you to do....

EDIT: if you change the permissions of that dir you could also use it to put your downloads in.
```
sudo chmod 775 /**dir path**
```
But I wouldn't do that either... Just because of the security of your system

---

### Post by helphope on 2006-05-22
Thanks a lot
For sure  I seem to learn more with every posted message... 

You were right. The file moved to the new directory:) :)

---

