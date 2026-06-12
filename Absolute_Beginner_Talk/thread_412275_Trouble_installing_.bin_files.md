---
title: "Trouble installing .bin files"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-04-17
I just downloaded planeshift and it is a .bin file. I am new and have no clue how to install it. I need some help.

	](*,)

---

### Post by Clay_Banger on 2007-04-17
make sure the file is on the desktop
using the terminal type:
```
cd ~/Desktop
sudo chmod +x *.bin
./nameofbinfile.bin
```

---

### Post by igknighted on 2007-04-17
> **Clay_Banger said:**
> make sure the file is on the desktop
using the terminal type:
```
cd ~/Desktop
sudo chmod +x *.bin
./nameofbinfile.bin
```

In general, any binary will be run like that.  However, many have specific instruction included on the website they came from, or included in the TAR archive they came in.  Always look for any file named README or INSTALL for specific instructions.

---

### Post by Istonian on 2007-04-17
There was no read me file, but Clay_Banger's suggestion helped. It installed fine.

---

### Post by crispy_420 on 2007-04-17
Or in English:

go to directory
make executable
run file

It does not have to on your desktop, it can be any directory. So for example, I am really crazy about keeping files in order. So if I download a firefox installer(call it firefox.bin for an example here), it goes in /home/software/internet/firefox.

So then you can cd, direct terminal to that directory.

> cd /home/software/internet/firefox

Now that I am that directory, as far as terminal is concerned. You will want to make it executable. Two ways to do it, terminal or GUI. You don't need to sudo to make it executable as it is your own file and you have all rights.

Terminal:
> 
chmod +x firefox.bin

GUI:

Right click -> Properties -> Permissions
Make sure "Owner" is Read, Write & Execute
Close window.

Now for the install. Some programs need root and some just want to install for the user. I'll assume you'll need root as most programs do. 

In terminal do this:

> sudo ./firefox.bin

password

That sums it up.

---

### Post by slotdoctor on 2007-05-22
This was a very helpful post.  Wish there are more posts like this one!

Thanks,
Mario

---

### Post by Tethtibis on 2007-05-30
Crispy, that was a VERY helpfull post, but sometimes, the file is "owner" restricted, and since you installed it as root, you have to log into root. I've found, and the login screen, "for xubuntu" you have to push cntl + alt+ f1 all together, to get the terminal line, then type sh untill all you see is the $ symbol, then type "su login" or "su login root" whichever, set root as login and type your password, then type "chown -hR "username to change permission to" /"folder you want root permission taken off of. then you will have access. :O) I did this for Planeshift install on Xubuntu 7.04

---

### Post by skeeterflea on 2007-07-25
I must be an idiot...

I've done all of the recommendations here, and from other places, and I still cannot get the .bin to run.

```
~/Desktop$ ./PlaneShift_CBV0.3.019-x64.bin
bash: ./PlaneShift_CBV0.3.019-x64.bin: cannot execute binary file

```

---

### Post by helmethedd on 2007-12-17
I'm using dapper drake, and having the same problem. i'm trying to install Planeshift as well.
I've gotten the file downloaded to my desktop and can't get it to do anything. I've searched and searched for EASY TO FOLLOW (non-verbose) instructions on this.
i'd welcome someone to contact me via gmail or yahoo messenger using helmethedd.
I'd really like to give linux a fair shake at being able to do the same stuff as microsoft. But, if i'm gonna need a degree in computer science, then forget this!

---

### Post by diatribe on 2007-12-17
you probably need to do chmod +x name_of_file

---

### Post by diatribe on 2007-12-17
> **skeeterflea said:**
> I must be an idiot...

I've done all of the recommendations here, and from other places, and I still cannot get the .bin to run.

```
~/Desktop$ ./PlaneShift_CBV0.3.019-x64.bin
bash: ./PlaneShift_CBV0.3.019-x64.bin: cannot execute binary file

```

also are you running 64bit?

---

