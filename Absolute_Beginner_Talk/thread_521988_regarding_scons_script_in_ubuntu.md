---
title: "regarding scons script in ubuntu"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by cnu_sree on 2007-08-10
i am using scons to bulid "so's" for my project.
sucessfully built in fedora and suse same code when i try to complie here am getting the errors
they are
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers
<command line>:1:1: error: macro names must be identifiers

y like this .

thank u,inadvance
sree

---

### Post by AlexenderReez on 2007-08-10
have you check do you have compulsory library for scons...?unlike fedora and suse ,ubuntu comes with only important basic running system....you need to install additional compiler for some kind of script .....

---

### Post by splintercellguy on 2007-08-10
Perhaps you need to obtain build-essential? sudo apt-get install build-essential

---

### Post by cnu_sree on 2007-08-10
i installed all libraries for scons.
and i tested by buliding one simple so.
but im my original code showing some errors

---

