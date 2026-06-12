---
title: "Efficient Networks SpeedStream 5200 DSL Modem"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by porkfilledbutcher on 2005-07-08
:-x [FONT=Times New Roman]*[SIZE=3]How do I configure my modem? DHCP failed during installation. I tried "sudo pppoeconfig" but it rejected my password.[/SIZE]*[/FONT]

---

### Post by aragorn2909 on 2005-07-08
One question first, is this one all-black, or is it an older model with the clearish/whitish face where the lights are?

---

### Post by trash on 2005-07-08
I have the 5260, i've never had that problem though... are you filling in the username with:

[email]yourusername@yourisp.com[/email]

---

### Post by Umbra on 2005-07-08
first setup your root password.

sudo passwd root
(specify password)

the excecute the sudo pppoeconf

follow the instructions, i have the same dsl modem, and it worked fine for me.

---

### Post by aragorn2909 on 2005-07-08
[QUOTE=Umbra]i have the same dsl modem, and it worked fine for me.[/QUOTE]

2 different kinds of 5200

---

### Post by porkfilledbutcher on 2005-07-08
:neutral: [FONT=Times New Roman][SIZE=3]*It's black and silver. When I typed "sudo pppoeconfig", it didn't ask for a username - only a password.*[/SIZE][/FONT]

---

### Post by CyberTF on 2005-07-08
Ubuntu does something that most other distro's do not do automatically. It adds the initial user to the sudoers list and does not allow the user to initially set a root password. This makes for a little confusion though as a lot of new llinux users do not understand sudo.

Sudo is an acronym for Super User Do which is basically allowing you to run a command as the super user (root). sudo does prompt for a password but it is not asking for the root password. What it wants is the users password. It then checks to see if the user is allowed to run sudo and puts an entry in a log file for security review by root.

So what you'll want to do is type sudo pppoeconfig and then enter your own password. It will then run the command fine.

Alternatively you could do the following..

sudo passwd
enter your password if prompted by sudo
it will ask for a new password. Here it wants a new password for root
enter the new root password and press enter
re-enter the same password again and press enter
the new root password is now set

now you can enter a root shell at anytime by typing su- and then enter (notice the -)
this changes to the root user and enables the root environment. then you can run any command as you normally would without needing to use sudo.

I do not recommend the second way as it is very easy to make changes to the system and cause bad things to happen.

Hope this helps a little =)

---

### Post by trash on 2005-07-08
try:

'sudo pppoeconf'

not config


EDIT: sorry, I didn't get that it was a problem with your ubuntu password, i just assumed it was a problem with your ISP user password. last post should fix ya right up.

---

### Post by porkfilledbutcher on 2005-07-08
:-? [FONT=Times New Roman][SIZE=3]*Thanks for the help! I got past the password part, but it told me something along the lines of "command not found". I'm guessing it's because I typed **sudo pppoeconfig** instead of **sudo pppoeconf**.*[/SIZE][/FONT]

---

### Post by porkfilledbutcher on 2005-07-08
:| [FONT=Times New Roman][SIZE=3]*What will happen after I type sudo pppoeconf? What will I need to know about my modem and/or DSL account? Thanks a lot!*[/SIZE][/FONT]

---

### Post by orbz on 2005-08-30
I have this same modem and searching the only help i've been able to find is "use pppoeconf" but i gather that doesn't really work if ive got it connected via usb rather than an ethernet card?
is that true?
or is the issue perhaps that the system doesnt comprehend that the modem is there? (it definitely sees the device and identifies it by name, but i'm not sure whether it understands that it's a modem)

do i seriously need to buy an ethernet card for this? cause if i need to buy an ethernet card and/or a new printer (lexmark x85, 'nuff said) then i may as well just give my windows partition its space back because i dont have money for hardware and at this point ubuntu is basically totally useless to me

---

