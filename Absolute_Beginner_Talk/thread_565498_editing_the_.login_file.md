---
title: "editing the .login file"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by aas452 on 2007-10-02
Hi all

I am a new user to linux and am downloading a program which directs me to edit the .login file. Is this something you do for each program you download? Because when I try to run the program it the system doesn't see it. Can anyone direct me to the .login file or a website on the basics of downloading programs in linux?

Thanks a million

---

### Post by cmnorton on 2007-10-02
I think you're being directed to edit .bash_profile in your home directory /home/<your-login-name>. I've installed tons of stuff and never had to do this. Usually programs go into areas that are already part of your PATH.

What is the program?

---

### Post by nvteighen on 2007-10-02
> **aas452 said:**
> Hi all

I am a new user to linux and am downloading a program which directs me to edit the .login file. Is this something you do for each program you download? Because when I try to run the program it the system doesn't see it. Can anyone direct me to the .login file or a website on the basics of downloading programs in linux?

Thanks a million

Downloading & installing in GNU/Linux is normally done through the so-called "repositories". These are archives located at servers that allow you to download and automatically install things without any editing or anything else.

Each GNU/Linux distribution usually has its own repository/ies, and Ubuntu has a very complete one. You can access these repositories by four different ways, but to keep it simple, i'll show you the two graphical ones:

1) Go to the Applications menu. You'll see something called "Add/Remove Programs". Quite easy to use and will introduce you to the repositories idea. It is meant to be used only for simple tasks and does not offer everything on the servers.

2) Go to System --> Administration --> Synaptic Package Manager. This will show anything located at Ubuntu's servers. Easy to use, also; right-click what you want to install and select the option at the context menu.

This both programs are also used to remove programs you have installed using them. The good thing is that all four "package managers" use the same database, so if you install something with Synaptic, you can remove it with any other one you like. Also, repositories allow automatic updates of software you have installed through them.

People sometimes add new repositories depending on their needs, but it needs a bit of configuration file editing (not too difficult actually). So, in summary, we almost never download things from websites unless there's no other way, specially because Ubuntu repositories are really complete.

---

### Post by aas452 on 2007-10-03
hey guys thanks for the incite--

The site I want to download from gave me some specific instructions and maybe if I share them the outcome of what i really want to do will be a little clearer----

here are the instruction from Side Effects

[http://license.sidefx.com/help.php?platform=linux&commercial=no&mode=quickinstructions](http://license.sidefx.com/help.php?platform=linux&commercial=no&mode=quickinstructions)

I got up to the last part in ---- Installing Houdini

but I am not clear on how to run the program or what even going on internally with the installation --- any clarification would be awesome.

---

### Post by aas452 on 2007-10-03
ok figured it out, dumb me!!!

still having a problem finding the .login file seems I have to initialize Houdini's environment and then i will be able to run the program --

---

### Post by Terl on 2007-10-03
I looked at the link you provided.

I think the earlier entry was correct, they mean either bash-profile or your .bashrc file.  I would add it to the user's .bashrc file.  (In your home folder, the . makes it a hidden file.)

---

### Post by aas452 on 2007-10-03
got it to work ----- thanks a million

---

