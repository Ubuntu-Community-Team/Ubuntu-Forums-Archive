---
title: "ssh"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by bellzii on 2007-07-27
ive got that device that can connect 2 computers wirelessly, i wanted to use scp to move file .
Ive been following the instructions at  
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

but when i first started the test using the GUI from GNOME it worked well but asked for authentication , the window said "you must log in to bellzii@192.168.200.2 " and its asking for a password, bellzii is the computer im connecting from and the ip 192.168.200.2 is where i want to connect to.
I  tried both root passwrods but its not working
can someone help?
thanks for your time

---

### Post by rich.bradshaw on 2007-07-27
Don't use the root password, as you are connecting to bellzii@192.168.200.2, not root@192.168.200.2.

Use the password for bellzii.

If you are using the connect to server dialog in places, you won't get any confirmation if it works, but it will appear in the places menu next time you look.

---

### Post by Mornedhel on 2007-07-27
If there is no bellzii user on the server, you can't log on as bellzii, either. In that case, bellzii would be the default if you didn't provide a different username and are logged (locally) as bellzii.

---

### Post by rich.bradshaw on 2007-07-27
Yeah, I assumed both computers are yours, and both have a user called bellzii.

Obviously you might have to change that!

---

### Post by bellzii on 2007-07-27
ya both are mine but one is called bellzii  with ip 192.168.200.1, the other is doomic with ip 192.168.200.2 , when you said password what password do u mean is it the one i use to log in and to change to root?

heres a trial

root@bellzii-desktop:/home/bellzii/Desktop# scp me.txt bellzii@192.168.200.2:new/
bellzii@192.168.200.2's password:

it asks again for the password?

is the "new" the folder on the other computer doomic, how can i specify the directory as the desktop as an example?

---

### Post by Mornedhel on 2007-07-27
When you ssh something@somewhere, 'something' is the distant user's login.

I have an account on my school's network (well I'm an IT student, so we all have one), let's say my username on that network is foo (obviously not, but I'm not posting my login info here...), I'd ssh something like ssh [email]foo@servif-baie.insa-lyon.fr[/email] (servif-baie being that particular server I'm trying to ssh).

It so happens to be that my username on my own computer is the same as my username at school, so if I just ssh servif-baie.insa-lyon.fr, I'll be asked the password for that username (because it's mine on my computer - it could ask me for the password for i_see_blue_elephants if that were my login, obviously it wouldn't be the distant server's name...)

You don't have to use your administration password, you have to use the bellzii one (or the one for the user you are trying to 'impersonate' on the distant computer).

---

### Post by rich.bradshaw on 2007-07-27
To keep it simple try:

ssh doomic@192.168.200.2

then enter doomic's password on the remote pc.

(You are connecting to 192.168.200.2 as doomic)

You should get a shell prompt, type 

whoami

and you should be doomic.

exit

will get you back to your local pc.

I wouldn't use scp unless you are scripting, why not use the GUI method...

go to Places/Add Server

enter the IP, port 22, password or whatever it needs, then go to Places, and the server will be there, clcik it and it will open in Nautilus.

Much easier if you ask me!

---

