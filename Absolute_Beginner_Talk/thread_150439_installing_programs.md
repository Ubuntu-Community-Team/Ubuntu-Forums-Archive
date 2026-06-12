---
title: "installing programs"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by morwyn on 2006-03-26
I'm still trying to understand how to install programs in linux. I understand synaptic, but what about programs you download from the internet? how do you install them? i'm still grasping the idea that there is no equivalent to exe. i'm assuming i'll need to  use a terminal, but what exactly? thanks for your patience...

---

### Post by bionnaki on 2006-03-26
read this: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by morwyn on 2006-03-26
thanks for the link! I am sure I will need it in the future. Unfortunately, I am trying to install a .sh file, whatever that is... when i click on the .sh install file, it says "the file is a binary, saving it will result in a corrupt file." I'm not really sure what to do. (I am trying to install the trial of CrossOver).

---

### Post by darf681 on 2006-03-26
I think you install like so:
(example)
sudo sh /media/cdrom/ut2004.sh

so yours would be

sudo sh /[filepath]/[filename.sh]

---

### Post by Mustard on 2006-03-26
[QUOTE=morwyn]thanks for the link! I am sure I will need it in the future. Unfortunately, I am trying to install a .sh file, whatever that is... when i click on the .sh install file, it says "the file is a binary, saving it will result in a corrupt file." I'm not really sure what to do. (I am trying to install the trial of CrossOver).[/QUOTE]
Normally these types of installs come with a README or INSTALL file giving instructions.

---

### Post by gigi1234 on 2006-03-29
Hi. I believe I just successfully installed the Crossover demo in Ubuntu Breezy.

1. Download the .sh file from the Codeweavers website

2. In the terminal:

           $ sudo su

           $ ls (check that you are in the directory where the .sh file is, if not cd to  
                   that directory)

           $ install-crossover-standard-demo-5.0.1.sh


3. That's all there is to it.  A installer GUI will start and you will accept the license agreement and then it will install. Good luck!!!

---

### Post by xXx 0wn3d xXx on 2006-03-29
[QUOTE=gigi1234]Hi. I believe I just successfully installed the Crossover demo in Ubuntu Breezy.

1. Download the .sh file from the Codeweavers website

2. In the terminal:

           $ sudo su

           $ ls (check that you are in the directory where the .sh file is, if not cd to  
                   that directory)

           $ install-crossover-standard-demo-5.0.1.sh


3. That's all there is to it.  A installer GUI will start and you will accept the license agreement and then it will install. Good luck!!![/QUOTE]


Try this for installing .debs. It allows you to double click a .deb file and install it. [ Here is the tutorial. ](http://ubuntuforums.org/showthread.php?t=114215)

---

