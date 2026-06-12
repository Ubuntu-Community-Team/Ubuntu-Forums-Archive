---
title: "Hello"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Nitehawk on 2007-06-28
Hello to all!

I am new to linux as a whole, but like to experiment with new (new to me) things.

I have Ubuntu installed on a laptop. Install was uneventful, even the wireless lan connection went without a hitch.

My biggest snag now is I am trying to use the browser as I did in Windows (am I allowed to say that :) )  However, because of the entire root user syntax, I am unable to add shockwave, flash player and other addons to the browser.  All the instructions have me using terminal, but the folders I need to , want to , install too are restricted to me.  I am not familiar with the linux command line yet, but I know how to follow instructions.  Any advice would be helpful.

I will keep looking on my own and probably find the answer eventually, but.... You know how that goes.

Anyway, just wanted to say hello and all the good stuff.

Later

---

### Post by overdrank on 2007-06-28
> **Nitehawk said:**
> Hello to all!

I am new to linux as a whole, but like to experiment with new (new to me) things.

I have Ubuntu installed on a laptop. Install was uneventful, even the wireless lan connection went without a hitch.

My biggest snag now is I am trying to use the browser as I did in Windows (am I allowed to say that :) )  However, because of the entire root user syntax, I am unable to add shockwave, flash player and other addons to the browser.  All the instructions have me using terminal, but the folders I need to , want to , install too are restricted to me.  I am not familiar with the linux command line yet, but I know how to follow instructions.  Any advice would be helpful.

I will keep looking on my own and probably find the answer eventually, but.... You know how that goes.

Anyway, just wanted to say hello and all the good stuff.

Later
Hi and welcome, you can say windows  some still use windows and other OS. Could you tell us what browser you are trying to use?:)

---

### Post by Seisen on 2007-06-28
I can tell you right off the bat that shockwave player is not  available in Linux as of yet, hopefully one day.

---

### Post by speaker219 on 2007-06-28
Mmm, if you're using firefox without flash player insalled, the easiest method to get flash and install it would be to  go to a youtube video page, and then there will be a bar that pops up in firefox saying you have plugins missing. Then click "install missing software" and flash player will be automatically downloaded and installed in firefox. If you wanted to do it in terminal, you would need to use "sudo" before the command to install the plugin to give you root user permissions, although I don't think you should have to do that to install flash, so be careful.

---

### Post by Tomosaur on 2007-06-28
When using the command line, if you need access to restriced directories, then just use the 'sudo' prefix:

```

sudo cp ./myFile /etc/myFile

```

```

sudo aptitude install my_program

```

etc etc

The sudo command will ask you for your password, but you will **not** see it being typed, so be sure to spell it correctly :)

---

### Post by iver2435 on 2007-06-28
One other thing that might help you along is to install the "Ubuntu Restricted Extras" package available under "Add/Remove Programs..." off the "Applications" menu.  It's in the "Other" category, or you can just search for it by name.

Be sure to read the disclaimer that is displayed before installing this package carefully, as it involves some important legal stuff.

The Restricted extras package includes a bunch of cool stuff that you'll probably eventually want to have, like the JRE and some other cool things.

---

### Post by speaker219 on 2007-06-28
> **iver2435 said:**
> Be sure to read the disclaimer that is displayed before installing this package carefully, as it involves some important legal stuff.

:roll::lol:

---

