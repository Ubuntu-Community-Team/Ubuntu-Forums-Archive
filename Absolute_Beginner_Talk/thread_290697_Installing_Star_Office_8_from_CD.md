---
title: "Installing Star Office 8 from CD"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by ArtificerJon on 2006-11-01
I am a complete newcommer to Linux and Ubuntu having lived with "That other OS" for more years than I care to mention.  I am determined this time to convert to Ubuntu/Linux having made a false start several years ago when my lack of knowledge stalled me.  It is still getting in the way as I have purchased Star Office 8 and have it on CD but cannot find how to install it from CD as the instructions which come with it don't seem to align with Ubuntu I am running 6.06. (Actually I am running "That other OS" on this old PC untill I am happy with using Ubuntu when my better (?) PC will get converted).

Can anyone help me with easily understood instructions for installing Star Office 8 from CD please.

---

### Post by taurus on 2006-11-01
What does it exactly tell you to run to install it?  It would be great if you can at least list the commands that it tells you to do!  Otherwise, you can always use OpenOffice 2.0!!!

---

### Post by raqball on 2006-11-01
Does it tell you to ./compile, /make, or ./setup

???

Never used it so I am guessing here

---

### Post by ArtificerJon on 2006-11-01
OK thanks here goes with the instructions in the Getting Started Guide for installing on Linux, I will try and type them verbatum but please forgive any obvious errors :

1. **Open a shell or terminal window** *(this I can do !)*
2. **Enable graphics display for the superuser.**
   As a normal user, enter the following command:
   [FONT="System"]xhost +[/FONT]
3. **Become superuser.**
   Enter [FONT="System"]su -[/FONT] to become superuser. *(Should  I use [FONT="System"]sudo[/FONT] at this point ?)*
4.**Set he DISPLAY variable to point to your machine.**
   Enter the following command:
   [FONT="System"]export DISPLAY=your_machine_name: 0.0[/FONT] (not sure if there is a space before 0.0)
5. **Change to the directory that contains the StarOffice 8 installation program.**
6. **Start the setup script.**
   Enter the following command:
   [FONT="System"]./setup[/FONT]
7. **Follow the instructions.**

---

### Post by ArtificerJon on 2006-11-01
Please see my reply to the previous response

Thanks

---

### Post by taurus on 2006-11-01
> **ArtificerJon said:**
> OK thanks here goes with the instructions in the Getting Started Guide for installing on Linux, I will try and type them verbatum but please forgive any obvious errors :

1. **Open a shell or terminal window** *(this I can do !)*
2. **Enable graphics display for the superuser.**
   As a normal user, enter the following command:
   [FONT="System"]xhost +[/FONT]
3. **Become superuser.**
   Enter [FONT="System"]su -[/FONT] to become superuser. *(Should  I use [FONT="System"]sudo[/FONT] at this point ?)*
4.**Set he DISPLAY variable to point to your machine.**
   Enter the following command:
   [FONT="System"]export DISPLAY=your_machine_name: 0.0[/FONT] (not sure if there is a space before 0.0)
5. **Change to the directory that contains the StarOffice 8 installation program.**
6. **Start the setup script.**
   Enter the following command:
   [FONT="System"]./setup[/FONT]
7. **Follow the instructions.**

Then open a terminal, Applications -> Accessories -> Terminal, and change to where your CD-ROM is mounted.  Then run the setup script to install it...

```

cd /media/cdrom0 (assuming your CD-ROM is mounted in /media/cdrom0...)
sudo ./setup (use the same password that you use to log in...)

```
Also, make sure you have installed java first because it will check to see if you have a running java on your machine...

---

### Post by Peter The Plumber on 2006-11-23
> **ArtificerJon said:**
> I am a complete newcommer to Linux and Ubuntu having lived with "That other OS" for more years than I care to mention.  I am determined this time to convert to Ubuntu/Linux having made a false start several years ago when my lack of knowledge stalled me.  It is still getting in the way as I have purchased Star Office 8 and have it on CD but cannot find how to install it from CD as the instructions which come with it don't seem to align with Ubuntu I am running 6.06. (Actually I am running "That other OS" on this old PC untill I am happy with using Ubuntu when my better (?) PC will get converted).

Can anyone help me with easily understood instructions for installing Star Office 8 from CD please.

  Please see this thread for instructions <http://ubuntuforums.org/showthread.php?p=1799419#post1799419> specific to the cd install. Please not I did not do the following which might explain why I had to manually put the links and icons in?

 Originally Posted by ArtificerJon  View Post
OK thanks here goes with the instructions in the Getting Started Guide for installing on Linux, I will try and type them verbatum but please forgive any obvious errors :

1. Open a shell or terminal window (this I can do !)
2. Enable graphics display for the superuser.
As a normal user, enter the following command:
xhost +
3. Become superuser.
Enter su - to become superuser. (Should I use sudo at this point ?)
4.Set he DISPLAY variable to point to your machine.
Enter the following command:
export DISPLAY=your_machine_name: 0.0 (not sure if there is a space before 0.0)
5. Change to the directory that contains the StarOffice 8 installation program.
6. Start the setup script.
Enter the following command:
./setup


  Good Luck!

Regards,

Peter

---

