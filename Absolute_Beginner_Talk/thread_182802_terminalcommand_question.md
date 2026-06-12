---
title: "terminal/command question"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-05-26
erm is there a file on me hd that lists the ex.@ubuntu in the terminal or is there a way i can set it to say what ever i want for **all** users?

---

### Post by Koech on 2006-05-26
Should be but never heard of it.

---

### Post by Ben Sprinkle on 2006-05-26
ya...any1 know the command or file!?!](*,) :-k

---

### Post by Mustard on 2006-05-26
I know that for a single user the command prompt is configured in the **.bashrc** file in your $HOME directory.  I'm not sure how you would do it for all users, nor am I familiar with the correct syntax to configure it.  If you are going to muck around with it, I would at least backup the original first.

-edit-

The system-wide configuration seems to be in the /etc/bash.bashrc file.  Again I would recommend you proceed with caution. :)

---

### Post by Ben Sprinkle on 2006-05-26
actually all u had to type was sudo hostname *name* but dunno if system wide,,

new question when i am at the console login screen how do i change the @ubuntu part? NOTE:this isnt for ubuntu its for a live cd im making based on it

---

### Post by Koech on 2006-05-26
Just by changing your hostname at System>Administration>Networking tab for hostname. Or you can do otherwise to change the name of your machine. The name after @ represents the name of your box. It seems you installed using default values.

---

### Post by Sutekh on 2006-05-26
If you are still at the console try editing the /etc/hostname and /etc/hosts files to reflect the new hostname, then use sudo hostname <newhostname>

---

### Post by Ben Sprinkle on 2006-05-26
i tried these...does in the lilo.confg file the label part make it say it in console at main bootup screen?

---

