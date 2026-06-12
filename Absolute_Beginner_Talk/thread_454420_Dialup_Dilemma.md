---
title: "Dialup Dilemma"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-05-25
Howdy all:

I'm running Feisty on a Dell Insiron laptop, with a Conexant modem. I've accessed the Net via wireless and ethernet wire, but never dialup, and I can use your help with that.

I believe I installed the Linuxant (free version) soft modem driver correctly. I also installed wvdial and gnome-ppp. I am using the correct phone number, username, and password. The ISP has verified this.

With gnome-ppp, it dials, does the handshake, connects for ONE second, then drops off. This happens when I check the "Remember Password" box in gnome-ppp. Then, like I said, it connects for one second, then dies.

When I do NOT check the "Remember Password" box in gnome-ppp, this box appears (attached jpg screen shot), and just sits there. Nothing else happens.

The ISP says that when I try to connect, the password field is BLANK. They are not receiving the password. They said everything else seems okay.

I added the phone number, username, and password to the wvdial.conf file. When I try to connect with wvdial, I get the following:
________

rich@rich-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT7182242
--> Waiting for carrier.
ATDT7182242
CONNECT 57600 
--> Carrier detected.  Waiting for prompt.
*------------------------------------*
*    Welcome to Frontier Internet    *
* Unauthorized Access is Prohibited  *
*------------------------------------*
User Access Verification
Username: 
--> Looks like a login prompt.
--> Sending: [email]blahblah@frontiernet.net[/email]
[email]blahblah@frontiernet.net[/email]
Password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authorization failed.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT7182242
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT7182242
--> Waiting for carrier.
ATDT7182242

For some reason the ISP is not receiving the password. Any suggestions?
Thank you.

---

### Post by Bachstelze on 2007-05-25
Add a line in your wvdial.conf that says

```
Carrier check = no
```

---

### Post by RichPicker on 2007-05-25
Thanks.

I'll also read the instructions from here [https://help.ubuntu.com/community/Di...388d58d7add4f9](https://help.ubuntu.com/community/Di...388d58d7add4f9).

---

### Post by RichPicker on 2007-05-29
Changing the wvdial.conf file did not help.

I did fill in the username, password, etc. in Systen>Administration>Network. And after doing that, and dialing with gnome-ppp, it says I am connected, and the '00:00:00" counter says I am connected. But I can not get on the internet. I suspect I might be missing something simple like adding the info to Network. What else have I missed?

In the Ubuntu instructions, it say to "activate 'noauth' by removing comment sign" in kppp-options. But that file does not exist on this computer.

Your suggestions?

---

### Post by RichPicker on 2007-05-29
Hey Hey I got it ! ! ! Way Cool everyone.

I had to add "carrier check = off" to the $HOME/.wvdial.conf file.

And now I have dialup. Great.

Until next time. Thanks, and best to you.

---

