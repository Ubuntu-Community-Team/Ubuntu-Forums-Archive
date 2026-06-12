---
title: "Installing PlaneShift...."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-23
Hi,
I just downloaded the game PlaneShift. It looks cool so I thought I give it a shot.

Anyway the downloaded file is PlaneShift_CBV0.3.018.bin

So how do I install and run it? Does the install place it under Applications>Games ???


Thanks

---

### Post by Inxsible on 2007-06-23
I have never installed PlaneShift. But bin files are normally installed as follows:

1) Cd to the folder where you have downloaded the file.

2) ```
sudo chmod +x PlaneShift_CBV0.3.018.bin
```

3)```
 sudo ./PlaneShift_CBV0.3.018.bin
```

---

### Post by ROUBOS on 2007-06-23
So I installed the game using the following commands : 

cd ~/Desktop
sudo chmod +x *.bin
sudo ./nameofbinfile.bin

But now I cannot run the game or unistall it. :(

Permission Denied

---

### Post by Enverex on 2007-06-23
Erm, where did you download it from and how do they say how to run it?

---

### Post by ROUBOS on 2007-06-23
I downloaded it from the Game site.
It does not mention anything there.
I installed it ok. But during the install I might have made mistake and can now only run it as root.

If I could run the uninstall as root I could unistall the game and try again


EDIT >> Or could I change the permissions? And allow the non-root users to run the game?

---

### Post by ROUBOS on 2007-06-23
there are two files in /opt/Planeshift (install directory)

they are:
uninstall
Uninstall Planeshift.desktop

which one is the right uninstaller and how do I run it?

EDIT >>> OK I uninstalled it using ./uninstall

Why do we have to type ./uninstall and not just uninstall to run it???

---

### Post by Enverex on 2007-06-23
"uninstall" would run an uninstall command on your machine ./uninstall tells it to run the file named uninstall in that folder.

---

### Post by ROUBOS on 2007-06-23
OK installed again. It asked for users and I entered my username. The asked to enter permissions so I entered 777.
Looks like its working
:)

Not so fast LOL

Running the client but there is a problem with the graphics now :(

---

### Post by ROUBOS on 2007-06-23
OK I enabled the ATI Restricted Driver and the game works fine. My Beryl desktop does not work though.

---

### Post by Forumdude on 2007-07-05
I can't even start the game. ](*,) I changed the permissions and it wont start. All I get is:
 > /home/elampe/PlaneShift/./psclient: line 6: /home/elampe/PlaneShift/psc: cannot execute binary file
/home/elampe/PlaneShift/./psclient: line 6: /home/elampe/PlaneShift/psc: Success


---

### Post by bravemenrun333 on 2008-05-15
I get the "permission denied" too! how can i fix it? cant get into game folder to uninstall it, cause got no permission, it says... what can i do?

---

### Post by miznatt on 2008-05-21
All you should have to do it reinstall the .BIN without Sudo permissions, and during the process, don't select any of the options that mention 'root permission may be needed to do this' (something to that effect) and you should be fine :)

---

