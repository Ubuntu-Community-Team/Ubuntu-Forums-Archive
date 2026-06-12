---
title: "how to reset the root password"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by jasonaz on 2007-06-05
hey guys i just installed ubuntu 7.04 and its awesome but i have a dillema..how do i reset the root password since i forgot the password..idiot me for not rememberin but how do u reset it anyway

---

### Post by Catsworth on 2007-06-05
I seem to recall that Ubuntu doesn't have a root password by default, did you set a password for the root account or have you forgotten the password for your own (main) acount?

---

### Post by jasonaz on 2007-06-05
i think i set my own root password but i forgot it..i remember d other password which is d one i use to log on to the other account

---

### Post by Catsworth on 2007-06-05
You would know if you had set a root password or not, it isn't something that you can really do by accident.  Did you do it during the install process, or have you done it sunsequent to that?

What are you doing that is asking for the password?

---

### Post by jasonaz on 2007-06-05
i set a root password but yeh i forgot it already (pretty bad considerin im only 18 lol)...and im doin d sudo command to change d bootloader option to make windows xp the first on the boot list

---

### Post by wormser on 2007-06-05
For security reasons you do not want to access root.  Use sudo or gksudo (for graphical apps).

But, for you knowledge....

```
sudo passwd root
```

Ubuntu does not set up a root password during the install.  It generates a random password for root.  This is for security reasons and it is best if you follow this basic security rule and do not log into root.

---

### Post by milambyr on 2007-06-05
Can you do System -> Administration -> Users and Groups ?
Then click on Root and select properties, you can reset the password there.

---

### Post by Catsworth on 2007-06-05
Ok, sudo uses your account password, not the root password usually.

As you're asking the question, I'm guessing that you've tried your account password and it hasn't worked.

Try typing:

```
sudo passwd root
```

See if that helps, it will ask you for a password (this is the one for the account you are logged into), and then for the new password for the root account.

Like I say though, you're better off using sudo instead of logging in as root, and sudo uses your normal account password.

---

### Post by Catsworth on 2007-06-05
:D  

Beaten to it :D

---

### Post by McTek on 2007-06-05
wormser........ everybody needs help with Flash. Hope they get the 64 bit vertion done soon.

---

### Post by jasonaz on 2007-06-05
> **milambyr said:**
> Can you do System -> Administration -> Users and Groups ?
Then click on Root and select properties, you can reset the password there.
I know this is out of the main topic but I cant see the above mentioned menu on the admin menu as well

---

### Post by trusky5 on 2007-06-08
Hi,

I've got a simular problem. During installation i had to do some work in the house and was a bit absent, im not quiet sure about the user password anymore. and since i did not set up a root password i can not log in at all. What should i do???
Need quick help, my little cousin needs her computer for schoolwork. :(

Thanks

Jimmy

---

### Post by trusky5 on 2007-06-10
Hi again,

sadly but I managed to change the root password and the user password. Ive just booted into failsafe and "passwd" let me make a new password for the root user and "passwd user" the user password. i didnt even need a password to log in or change the password. That actually makes Linux even unsafer than Windows. just boot into failsafe and dont bother about any passwords???? how can i configure my machines to make them at least as "secure" as a M$ Windows machine??? Im using Ubuntu studio (if i havent mentioned it before).
I personally think that disabling the root acount is ok, but not asking the user during installation of the system for a root password is bull***t. whats that surposed to be good for??? id change that. And the gui for the system installation didnt work on any of my machines! is there one? (would be nicer)

Jimmy

---

### Post by Catsworth on 2007-06-11
By setting a root password you've actually made your system *less* secure.  Ubuntu doesn't have a root password by default, it isn't blank though (ie. no password neeed) it's actually 'null' (ie. no password can be entered so the account can't be logged in to) which means that you *can't login as root*.  By setting a password for the root account you have made it possibe to crack/guess/brute-force the password.

As for security.  Someone needs to have physical access to your Ubuntu box in order to boot it in failsafe mode.  If someone has physical access to your machine then they own it, there is nothing (apart from having some *seriously* strong encryption) that you can do to prevent them from having access to your machine/data.

---

### Post by trusky5 on 2007-06-11
But still, if i had my machine in a company or somewhere else, like if it was a "public" computer, anyone could mess it up. so thats why i think it is less secure than windows. even with windows' cd recovery tools you need a password. it would just be nice, that in failsafe you'd needed a root password or any other password to get in to the system.

your right with what you said about the root password, didnt think about that. but if, and that was what i thought before i found out that you dont need a root password for failsafe, you needed one youd have a big problem to get access to your machine.
is it possible to set up a password for failsafe??? if so, please let me know how.

thanks,
jimmy

---

### Post by Catsworth on 2007-06-11
> **trusky5 said:**
> But still, if i had my machine in a company or somewhere else, like if it was a "public" computer, anyone could mess it up. so thats why i think it is less secure than windows. even with windows' cd recovery tools you need a password. it would just be nice, that in failsafe you'd needed a root password or any other password to get in to the system.

your right with what you said about the root password, didnt think about that. but if, and that was what i thought before i found out that you dont need a root password for failsafe, you needed one youd have a big problem to get access to your machine.
is it possible to set up a password for failsafe??? if so, please let me know how.

thanks,
jimmy

The instructions [HERE]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_disable_all_interactive_editing_control_for_GRUB_menu") should help you secure your grub menu (and in turn stop people accessing the recovery options).  Note the use of the 'lock' key word within the grub menu to specify which options should be locked out.

You will also need to change boot orders in your BIOS to prevent it from booting from CD, and then you will need to password protect the BIOS as well.

Note though that *anybody* with unchecked physical access to the machine *owns* it.  Regardless of whether it's Windows/Linux.  I can gain access to the Administrator account of any Windows PC (barring heavy duty file encryption) in less than 5 minutes usually :D

---

### Post by trusky5 on 2007-06-11
True! ;)
I knew that you could set up a password for grup, just forgot that. but in my family i dont have to bother about anyone even using my computer. their all windows users. they wouldnt even recocnize grup, theyd think its part of the computers "bios-boot-up" sequence.

Anyway, thanks a lot.

---

