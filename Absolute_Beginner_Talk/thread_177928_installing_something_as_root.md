---
title: "installing something as root?"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by slimdog360 on 2006-05-17
Im trying to install multisim, an electronic circuit simulator, because its only made for windows im using wine to do it. When I try to do this though multisim says that it needs administrator privliges.
 Ive tried the following the advice form the ubuntu starter guide and a couple of other posts but they dont help/work. Ive also tried running it from the command line using 
        sudo wine setup.exe
but it still says the same thing. How do I login from the main login screen as the root user.
Thanks

---

### Post by Jimmey on 2006-05-17
Being root won't help. Sudo gives you root priveledges - It's the same as being root.

Try changing the permissions of the file.

> sudo chmod +x setup.exe

---

### Post by dickohead on 2006-05-17
I'm not sure that will change anything. It sounds like the program multisim is after admin privelages so it can install, is this correct?

For that you will need to alter your wine config somehow to install things as administrator.

If it is a local issue logging in as root will achieve nothing, as using sudo runs the command as root. You'll need to find out what needs admin privelages, multisim or wine and then figure out how to adjust them. It might also be that multisim just won't work with wine.

---

### Post by slimdog360 on 2006-05-17
yep different nothing happened, any ideas on how to find out what needs admin privelages?

---

### Post by hotbrainz on 2006-05-17
type in "sudo passwd root"

it will ask you to enter your new linux password... so enter your new
password

mind you everytime you login you have to 

su 
enter password to login as root

I hope this helps---

---

