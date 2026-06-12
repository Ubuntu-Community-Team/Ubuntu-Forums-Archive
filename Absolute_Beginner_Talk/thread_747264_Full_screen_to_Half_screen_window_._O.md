---
title: "Full screen to Half screen window ._O"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-04-06
Sometimes when running ubuntu apps that run in full screen, they will suddenly go to a half screen window. It seems consistent, so doesn't seem like I'm controlling it at all. Read somewhere that disabling compiz might do something,? If someone had this idea reading this, please could you tell me how to disable and enable compiz? tIA!

---

### Post by Mazza558 on 2008-04-06
You can create 2 buttons in the top bar to do this for you. 

Right click on the top bar and click "add to panel"

Choose "custom application launcher", and it'll come up with a new window.

In the name box, type something like "Disable compiz"

In the command box, type

> metacity --replace

Then choose an icon by clicking on the icon to the left.

Repeat these for the second icon (call it "Enable Compiz"), but this time, the command is:

> compiz --replace

For both buttons, ignore the "comment" box.

---

### Post by corney91 on 2008-04-06
Or you can install the [compiz icon]("http://lifehacker.com/software/linux/control-compiz-fusion-from-the-tray-293997.php") ;)

---

