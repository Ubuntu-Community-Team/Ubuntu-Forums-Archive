---
title: "Stressed with AIM"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by barqster on 2005-12-24
I've spent the past hour or so trying to install AIM on 5.1, I've been using Ubuntu for less than a day and was able to catch on pretty quick. But this AIM thing is making me crazy! :mad:  Please help.

---

### Post by barqster on 2005-12-24
Oh bye the way, I know I can use GAIM and all these other clients, but I'd like to stick with aim, so if you tell me how to install AIM that would be great!

---

### Post by estel on 2005-12-24
Where have you tried to install it from?

---

### Post by estel on 2005-12-24
From [http://www.aim.com/get_aim/linux/latest_linux.adp#install](http://www.aim.com/get_aim/linux/latest_linux.adp#install) I assume you're using the "install for other OS" option?

Do you have normal ubuntu for x86, or AMD64 one?

---

### Post by barqster on 2005-12-24
Yup, I've installed from aim.com (the linux .tgz) and I'm completely stumped, yes it's a normal system for x86, and I did click other OS

---

### Post by barqster on 2005-12-24
Am I supposed to move the extracted files anywhere? I have been downloading all of my tars in a downloads dir in home

---

### Post by estel on 2005-12-24
When sudo, try moving the file to / before extracting using tar.

---

### Post by barqster on 2005-12-24
OK, I'll try it right now

---

### Post by barqster on 2005-12-24
It's just blinking, I think that it's conflicting with the /usr already in the /

---

### Post by barqster on 2005-12-24
oops put tar xzvv instead of tar xzvf it iniated

---

### Post by barqster on 2005-12-24
Now I don't know where it went, it supposed to be in /usr/local/bin/aim. Oh wait I found it, it's in /usr/bin

---

### Post by ubuntuuser on 2005-12-24
YOU SHOULD ALWAYS BACKUP ANY FILES BEFORE OVERWRITING THEM!
Ok, here's an example of how to do it:

1. download the .tgz file to /tmp
2. unpack the file, a "usr" directory and several other subdirectories of usr are extracted
3. open a terminal window
4. type cd /tmp/usr
5. type sudo cp -R * /usr
6. If you are asked to overwrite any files, make a backup of the file before overwriting it
7. type aim to start aim

That should do it.

---

### Post by barqster on 2005-12-24
OK I got past the sudo cp -R * /usr, and then I typed aim, and I get the is error: "aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory"

---

### Post by barqster on 2005-12-24
Is anyone still there?

---

### Post by ubuntuuser on 2005-12-24
This one is tricky:

Install libstdc++2.10-glibc2.2 using synaptic or apt-get. Then type

cd /usr/lib
sudo ln -s libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2

Start aim.

---

### Post by barqster on 2005-12-24
Now it says cannot execute binary file......wow....

---

### Post by ubuntuuser on 2005-12-24
Now I'm stuck. Until now I had exactly the same problems, but symlinking helped me to execute /usr/bin/aim properly. I was even able to connect to their server. Do you get any more error messages? Maybe you could post them, too?

---

### Post by barqster on 2005-12-24
Well it's 8:00 and Christmas Eve, Time for tradition, that you ubuntuuser for your help. If you can help me anymore I'd be grateful. I will be checking my e-mail if you'd like to send me one; my e-mail is [email]christophe.rossie@gmail.com[/email]

Happy Holidays

---

### Post by barqster on 2005-12-24
oh your back, I'll try it a coupple more times before I go to the family.

---

### Post by barqster on 2005-12-24
Actually, I had a question; ok so I downloaded it into /tmp, then extraceted it into /tmp, then executed the command sudo -R * /usr, then downloaded the one file with sudo apt-get install, and I'm supposed to install the 2 files; which directory should I be in when I execute this command in the terminal?

---

### Post by ubuntuuser on 2005-12-24
Ok: /tmp is just my directory of choice for extracting things, could have been any other directory, too. With this sudo cp... thing you copied the extracted files to the path where AOL wants them to be. The package you installed with apt-get included  version of the libstdc++... file that was missed, but in a different version, so we had to create a symbolic link (think of it as a more sophisticated windows shortcut) to that newer version, but that link had to have the name of the older version. Now, as long as /usr/bin is in your $PATH environment variable (it usually is) you can type aim from anywhere you like.

[EDIT]
I misunderstood your question: When you do the ln -s... command, you need to be in /usr/lib
[/EDIT]

---

### Post by barqster on 2005-12-24
Wow, I totally missed it, for any future noobish mistakes like I did....When you type, "sudo ls -s ......" the ls is the letter LS not IS. I can't believe it, how stupid things can mess you up so bad!

---

### Post by ubuntuuser on 2005-12-25
To avoid such errors in the future: just mark the desired code with your mouse, then go to your terminal window and click the middle mouse button.

---

### Post by The Warlock on 2005-12-25
Um, you do realize that the official, AOL-made AIM client for Linux is several years out of date, right?

Seriously, use gaim instead. It does everything that AIM does except better, really.

---

