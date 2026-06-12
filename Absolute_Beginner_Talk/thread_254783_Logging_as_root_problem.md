---
title: "Logging as root problem"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Jimit87 on 2006-09-10
Ok so i press alt + crtl+ F1

a black screen comes up and askes me for "my username Desktop login"

i put in my username and press enter

"password" comes up,

i put in my password.
and says "loging incorrect"

then "my username desktop login" comes back and same thing.

What am i doing wrong? how do i solve it?
without loging in as root, i can't install my nVidia 3D driver.

Thank you.

---

### Post by bulldog on 2006-09-10
You can't login as a root by default.

Use your name and password like you did provide by the install.

Use sudo to get root privileges and do your install.

[Be sure CAPS isn't enabled]

---

### Post by Najand on 2006-09-10
> **Jimit87 said:**
> Ok so i press alt + crtl+ F1

a black screen comes up and askes me for "my username Desktop login"

i put in my username and press enter

"password" comes up,

i put in my password.
and says "loging incorrect"

then "my username desktop login" comes back and same thing.

What am i doing wrong? how do i solve it?
without loging in as root, i can't install my nVidia 3D driver.

Thank you.

Login as the username you installed ubuntu for the first time. Then use sudo to do administrative tusks... If still, you need root, use:
```
sudo passwd
```
and enter a new password for root and login using that password...
Remember login as root is very dangerous for your system. So avoid login as root for daily usage.
Another way to use "root" without password is:
```
sudo su
```
and then enter your password and continue without making new password for root account.

---

### Post by aysiu on 2006-09-10
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo) explains everything.

---

### Post by Jimit87 on 2006-09-10
483916]Ok so from one forum i found out that to install nVidia 3D driver i must do the following.

1.: ctrl+alt+f1
2.: login as root
3.: init 3
4.: chmod +x /home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
5.: ./home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
6.: now the installer is loaded just keep pressing next next next next next... at the end of driver isntall it will ask you if the installer should automaticly update your Xorg config file, choose yes. the installer will exit now.
7.: init 5

is that right?
this is what i did.
1) opened terminal
2) typed in
> sudo su
3) it asked me to type in my password and so i did.
4) the thing changed from "gates@gates-desktop:~$" to "root@gates-desktop:/home/gates#"
5) i typed in init 3 next to that and pressed enter
6) nothing happend and i got that [email]root@...gate[/email]s#" back so then i typed in c> chmod +x /home/gates/NVIDIA-Linux-x86-1.0-8774-pkg1.run and pressed enter.
7) nothing happend and i got that [email]root@.....gate[/email]s# back so then i typed in > ./home/gates/NVIDIA-Linux-x86-1.0-8774-pkg1.run and pressed enter.
8 ) and i got this error mess. > bash: ./home/gates/NVIDIA-Linux-x86-1.0-8774-pkg1.run: No such file or directory

my nvidia driver is in the /home/my username forlder.

what am i doing wrong?

---

### Post by Jimit87 on 2006-09-10
ne one can help me with this problem?

---

### Post by Najand on 2006-09-10
> **Jimit87 said:**
> 483916]Ok so from one forum i found out that to install nVidia 3D driver i must do the following.

1.: ctrl+alt+f1
2.: login as root
3.: init 3
4.: chmod +x /home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
5.: ./home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
6.: now the installer is loaded just keep pressing next next next next next... at the end of driver isntall it will ask you if the installer should automaticly update your Xorg config file, choose yes. the installer will exit now.
7.: init 5

is that right?
this is what i did.
1) opened terminal
2) typed in

3) it asked me to type in my password and so i did.
4) the thing changed from "gates@gates-desktop:~$" to "root@gates-desktop:/home/gates#"
5) i typed in init 3 next to that and pressed enter
6) nothing happend and i got that [email]root@...gate[/email]s#" back so then i typed in c and pressed enter.
7) nothing happend and i got that [email]root@.....gate[/email]s# back so then i typed in  and pressed enter.
8 ) and i got this error mess. 

my nvidia driver is in the /home/my username forlder.

what am i doing wrong?

Well, it seems you don't really need root privilege...
Just try: 
```
sudo ./home/your-linux-username/NV and then push TAB
```

---

### Post by Najand on 2006-09-10
> **Jimit87 said:**
> 483916]Ok so from one forum i found out that to install nVidia 3D driver i must do the following.

1.: ctrl+alt+f1
2.: login as root
3.: init 3
4.: chmod +x /home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
5.: ./home/your-linux-username/NVIDIA-Linux-x86-1.0-8774-pkg1.run
6.: now the installer is loaded just keep pressing next next next next next... at the end of driver isntall it will ask you if the installer should automaticly update your Xorg config file, choose yes. the installer will exit now.
7.: init 5

is that right?
this is what i did.
1) opened terminal
2) typed in

3) it asked me to type in my password and so i did.
4) the thing changed from "gates@gates-desktop:~$" to "root@gates-desktop:/home/gates#"
5) i typed in init 3 next to that and pressed enter
6) nothing happend and i got that [email]root@...gate[/email]s#" back so then i typed in c and pressed enter.
7) nothing happend and i got that [email]root@.....gate[/email]s# back so then i typed in  and pressed enter.
8 ) and i got this error mess. 

my nvidia driver is in the /home/my username forlder.

what am i doing wrong?

Well, it seems you don't really need root privilege...
Just try: 
```
sudo ./home/your-linux-username/NV and then push TAB
```
If you got the same error, do
```
ls -al
```
and see if you have the file available and executable in your directory or not.

---

### Post by Jimit87 on 2006-09-10
> **Najand said:**
> Well, it seems you don't really need root privilege...
Just try: 
```
sudo ./home/your-linux-username/NV and then push TAB
```

first i typed sudo su and then taht thing changed to roo @ then i typed in init 3 pressed enter and then i typed in chmod +x /home/gates/NVIDIA-Linux-x86-1.0-8774-pkg1.run and pressed enter
but after i put that sudo ./home cmd and press tab nothing happend instead i hear s beep sound from my comp every time i preass tab
so i pushed enter and i got "sudo: ./home/gates/NV: command not found"

---

### Post by Najand on 2006-09-10
> **Jimit87 said:**
> first i typed sudo su and then taht thing changed to roo @ then i typed in init 3 pressed enter and then i typed in chmod +x /home/gates/NVIDIA-Linux-x86-1.0-8774-pkg1.run and pressed enter
but after i put that sudo ./home cmd and press tab nothing happend instead i hear s beep sound from my comp every time i preass tab
so i pushed enter and i got "sudo: ./home/gates/NV: command not found"

Do ```
ls -al
``` and see if the file is available or not?

---

### Post by Jimit87 on 2006-09-10
k never mind, there is no . in front of /home....

but then i get

but then after some loading adn all i get

Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 1.0-8774.......................................................................................................................................................................................................................................................................................

and new blue screen appears in term and this is the error mess. i get.

NVIDIA Software Installer for Unix/Linux





ERROR: Unable to find the system utility `ld`; please make sure you have the
package 'binutils' installed. If you do have binutils installed,
then

---

