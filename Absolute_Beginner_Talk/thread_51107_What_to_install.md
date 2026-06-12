---
title: "What to install"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by brunog on 2005-07-22
I am quite new to installing Linux (Ubuntu) packages.
I have noticed that every package is available for a different CPU? - wel at least I think this is what part of the name indicates.
For example:
i386 and amd64 and powerpc

On Synaptic package manager I have also notices packaged specificaly for Celeron and Pentium ii, iii and iv - packages ending with a 686?

How do I know what to install?

I am running a Intel Celeron 2.3 GHz PC
Do I install the i386 or the 686 packages?
Can you mix them up?

Some advice will be appreciated.

Thank you

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=brunog]I am quite new to installing Linux (Ubuntu) packages.
I have noticed that every package is available for a different CPU? - wel at least I think this is what part of the name indicates.
For example:
i386 and amd64 and powerpc

On Synaptic package manager I have also notices packaged specificaly for Celeron and Pentium ii, iii and iv - packages ending with a 686?

How do I know what to install?

I am running a Intel Celeron 2.3 GHz PC
Do I install the i386 or the 686 packages?
Can you mix them up?

Some advice will be appreciated.

Thank you[/QUOTE]


You can mix 686 and 386. You cannot mix those two with x86_64 though.

---

### Post by brunog on 2005-07-22
Thanks for the quick feedback.
I will install 686 if available - otherwise i386.

Something else:

I have tried the Ubuntu add-on CD, but think I messed things up.
When I close Synaptic it asks for a password (like when I open it) and then it just opens synaptic again.
Also the Filter on synaptic does not work.  No matter what filter I use - broken link for instance - it just lists all the packages.

Do I have to reinstall Ubuntu?

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=brunog]Thanks for the quick feedback.
I will install 686 if available - otherwise i386.

Something else:

I have tried the Ubuntu add-on CD, but think I messed things up.
When I close Synaptic it asks for a password (like when I open it) and then it just opens synaptic again.
Also the Filter on synaptic does not work.  No matter what filter I use - broken link for instance - it just lists all the packages.

Do I have to reinstall Ubuntu?[/QUOTE]

Can you open synaptic normally without the CD?

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

Plus...for EVERTHING on the CD...you can do it REAL quick with a little terminal work. (The terminal still exists in 2005 because its better for many things.)

If you want to go at it (I was nervious at first and now I love it), look at this guide:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

Be sure to read the notes at the top. It will work. Do this part first:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

A little copy and paste. Easy. Then type this command in a normal terminal:

sudo apt-get update

Then proceed to follow the guide...and everything wil work. Always has for me, and everyone else I've show the guide to (over 100 people).

---

