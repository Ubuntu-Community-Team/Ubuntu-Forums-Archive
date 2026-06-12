---
title: "~Help~ Total n00b here!"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by avgjoe22 on 2007-03-05
Okay.  I'm admitting this right off of the bat:
I suck at this.

I have NO CLUE how to install software.

I use the "./configure"

But i need "gcc"

So I follow the instructions.

And I suck at following these instructions, so I fail.

And I copy/paste commands on forums that I browse through.

And It says "Access Denied" or some such ****.

It appears to me that Ubuntu is better than Windows, but only for those who know it all to begin with!

[HELP]

I need a deep explanations of how exactly to install programs, compile code, etc.

Please, PLEASE make it idiot-proof.

:mad:

---

### Post by STREETURCHINE on 2007-03-05
what are you trying to install,

you may need to go into synaptic to install build-essentials,gcc or what ever else it is asking for

and give this a read.

   [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by Maestro23 on 2007-03-05
Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

How to Install: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

Beginner's Guide: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by konungursvia on 2007-03-05
It takes some perseverence, but you'll get there. Keep trying on the forum he showed you.

---

### Post by lavinog on 2007-03-05
> **avgjoe22 said:**
> Okay.  I'm admitting this right off of the bat:
I suck at this.

I have NO CLUE how to install software.

I use the "./configure"

But i need "gcc"

So I follow the instructions.

And I suck at following these instructions, so I fail.

And I copy/paste commands on forums that I browse through.

And It says "Access Denied" or some such ****.

It appears to me that Ubuntu is better than Windows, but only for those who know it all to begin with!

[HELP]

I need a deep explanations of how exactly to install programs, compile code, etc.

Please, PLEASE make it idiot-proof.

:mad:

Have you checked to see if the program that you want to install exists in synaptic package manager?
It would be alot easier and you would have less chances of having problems later.

---

### Post by oilchangeguy on 2007-03-05
also you can use automatix. go to [www.getautomatix.com](www.getautomatix.com)

---

### Post by avgjoe22 on 2007-03-06
Whoa, guys, sorry about the long reply!

Anyway, I am trying to install some applications (and Automatix helped a lot!), but I don't know when to use Synaptic, the .deb installer thing, or when I compile myself - it's the compiling that gets me.  Also, what is a dependency?  If it's what i think it is, can't I just get all of them for what I want at once, and if so, how?

---

### Post by jhenager on 2007-03-06
> **avgjoe22 said:**
> Whoa, guys, sorry about the long reply!

Anyway, I am trying to install some applications (and Automatix helped a lot!), but I don't know when to use Synaptic, the .deb installer thing, or when I compile myself - it's the compiling that gets me.  Also, what is a dependency?  If it's what i think it is, can't I just get all of them for what I want at once, and if so, how?

A dependency is a module or file that is depended upon for the program you are trying to install.
If it is missing, you get an error message because your software depends on it for some functionality.

Best way to install is either through Add/Remove Programs, or Synaptic. Both of these check for dependencies and install them for you. Automatix probably does this too, but I have found that it doesn't have the extensive list of programs the first two have. I really like Automatix, tho, for what it does.

---

