---
title: "Synaptic troubles"
date: 2004-11-17
forum: Apple PPC Users
---

### Post by trash on 2004-11-17
So I thought I would give Synaptic a try cuz so many people are talking about it but i've run into some problems...

first, I can't log in as root, even though my root password seems to be working everywhere else. My user password does log me in.. where do I change this?

Second, as my regular user I figured I could at least browse what packages are available but after selecting 'all' and doing refresh no packages are showing up at all.  I did check the repo list and they do exist.

any help please:)

---

### Post by sumanjay on 2004-11-17
This happens to be a documented bug in one particular version of Synaptic that has since been fixed. I suspect, that PPC users still don't have access to that version. Anyway, I ran into the same problem and there was an easy fix - locate .synaptic.conf files in your home directory and delete them. Then start Synaptic and it should be alright. I'll look up and check if there are any less destructive fixes.

---

### Post by sumanjay on 2004-11-17
I'm just curious - did you set up a root account? I thought Ubuntu avoided the creation of such an account for security purposes. Or at least, abstracted it away. I  use my user password to perform all administrative tasks, including installing packages thru Synaptic.

---

### Post by trash on 2004-11-17
thanks, yes i did set a root account.. can't remember how and it was before i found a howto so in all likelyhood it is not set with the proper permissions. I think i also diddled with the user/groups and I can't say i much understand them either lol.

I understand the security aspect no root account but lets face reality here, not one linux system installs perfectly, why not enable a root account and then stress the need to disable it AFTER it has been used, seems a little more logical no?

Ok so your advice worked perfectly:)... I lost control of things when i changed the default settings, so i guess i'll just leave it as is this time hehe.

cheers

---

### Post by ktindle on 2004-11-18
I have trouble with Synaptic too, but there are no .synaptic.conf files
in my home directory.

Synaptic simply displays nothing in the package list pane.

I need to download the kernel source package, so I can compile in
support for the Iomega ZIP drive in my beige G3, so it is a bit
upsetting to be unable to view the available packages.

The "Mark Update" function did work to apply security patches,
74 of them, but never have I seen a list of packages where they
should be.

---

### Post by trash on 2004-11-18
they are not in the users home directory, you'll find the Synaptic folder in the root directory... deleting the files totally worked, hope you have the same luck;)

---

### Post by sumanjay on 2004-11-18
Oops! I really ought to remember to put things in context - I assumed that trash would be using his root account and would delete the .synaptic.conf files that were there, and (gotta credit him for this!) trash caught on. Sorry about the mis-information - it really should be .synaptic.conf files in the root Synaptic directory.

---

### Post by trash on 2004-11-18
hey not a prob at all man, usually all it takes is a lil old push in the right direction. mucho thanks for the help:)

---

