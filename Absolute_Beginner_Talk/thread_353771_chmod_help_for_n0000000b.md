---
title: "chmod help for n0000000b"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by adza on 2007-02-05
could someone please help? I've installed ET, however it won't let me enable punkbuster.. i am putting this down to the file permissions on punkbuster.cfg only being set to read and write for the root user (but not execute?) so i'm trying to add write and execute permissions to all users using chmod.... the command 
sudo chmod a+wx /usr/local/games/enemy-territory/etmain/punkbuster.cfg
just returns me to the prompt (no error messages) however when i examine the file, the permissions haven't changed... have i got this syntax right? i am expecting this command to create write and execute permissions on that file for all users....???

please help me .... i'm a n0000000000b!! hehe

****edit***** it actually worked this way... i just needed to 'refresh' the window i was looking at the file through (through the 'places' bit).... sorry for posting this and wasting someone's time :( 

I wonder how to remove this post? admins?

---

### Post by hyper_ch on 2007-02-05
try:

```

sudo chmod 0777 /path/to/file

```

This will set rwx rights for everyone.

---

### Post by adza on 2007-02-05
thx sjau... :)

---

### Post by hyper_ch on 2007-02-05
did it work?

---

### Post by adza on 2007-02-05
i've got the file permissions sorted... however it didn't let me enable PB in game...
also sound don't work... sifting through threads now :P

---

### Post by adza on 2007-02-05
alright.. everything works except for sound... curiously enough though...
when i echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss as suggested, get a permission denied error.... i have set file permissions on this file for execute, even run as sudo... however still same error... i didn't think that i should be denied permission using sudo?

---

