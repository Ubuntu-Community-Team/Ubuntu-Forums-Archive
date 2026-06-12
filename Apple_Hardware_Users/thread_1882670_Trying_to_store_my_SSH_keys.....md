---
title: "Trying to store my SSH keys...."
date: 2011-11-17
forum: Apple Hardware Users
---

### Post by Wasteload on 2011-11-17
I have installed Ubuntu on a virtual box on my machine and have it up and running just fine.  I am following some instructions that are in a Web Design on Mac book.  I was able to get the key created just fine but when I run the commands that it says I need to run in order to store the keys it does not work.

These are the 2 commands that it says to run:

user$ ssd drew@x.x.x.x "mkdir .ssh; chmod 700 .ssh"

then

user$ scp .ssh/id_rsa.pub drew@x.x.x.x: .ssh/authorized_keys2

When I attempt to run the top command it tells me that there is no such file or directory? 
Any advice on this I would appreciate, I know that I dont HAVE to have those in there but I am making this to test my sites that I make and such so I would like to not have to type in that password everytime. 

Thanks in advance,
   Drew

---

### Post by lael on 2011-11-17
I use:
```
ssh-copy-id user@machine
```

---

### Post by Wasteload on 2011-11-21
Thanks a lot for getting back to me on that.  I tried to command that you suggested in the previous post:

ssh-copy-id user@host

And I got an error saying that there were no IDs there.  So I guess now my question would be what command should I type before that to create the IDs that it will see?

---

### Post by Wasteload on 2011-11-21
Anyone who may know what I need to enter along with the other code that was mentioned in order to create new keys.

---

### Post by lael on 2011-12-10
So you don't have an ~/.ssh/id_rsa.pub file?  

Try github's tutorial on generating keys (just the keygen parts).
[http://help.github.com/linux-set-up-git/]("http://help.github.com/linux-set-up-git/")

---

