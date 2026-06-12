---
title: "Bluetooth Woes in Feisty"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-05-20
Cheers,

Im trying to make bluetooth work in Feisty but I seem to have hit a brick wall.
When I try to connect from my CellPhone to my PC, my CellPhone asks for 
a PIN, so I type in 1234 which is I think the default but all I got is 
"Unable to pair.  Try Again?" so I tried 0000 for the PIN and still I get the same error
"Unable to pair.  Try Again?".

And when I looked at /etc/bluetooth/hcid.conf it says that passkey is indeed "1234".

And when I try to initiate the connection from the PC, my CellPhone asks for a PIN so I
typed in 1234, but Ubuntu gives me this error "Unable to connect to remote device."
and my CellPhone also gives me this error "Invalid Pin".

Any ideas on how to solve this??

My CellPhone is Samsung SGH-X820.

Thanks.

---

### Post by Inxsible on 2007-05-25
In the same file i.e. /etc/bluetooth/hcid.conf look for a line that says

security user;

Change that  to 

security auto;

and you should be able to pair your phone. You can change the passkey too. If you do, you need to reboot and then try with the new password.

Cheers !!

---

### Post by delphiguy on 2007-05-25
Thanks for the reply.  I finally got it working, I dont know how, but it worked.
I just installed anything that closely resembles blue or has blue in the package name in synaptic.

---

