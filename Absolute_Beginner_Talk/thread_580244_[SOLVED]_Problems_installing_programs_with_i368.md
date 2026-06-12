---
title: "[SOLVED] Problems installing programs with i368"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mitchbones on 2007-10-18
**EDIT:I have solved the problem. For anyone else with my misfortunes, go to System>Software Sources> and I turned checked some of them.**

Hello, I have former experience with Dabber Drake, and decided to start getting my feet wet again with Gutsy.


I am running with Intel's Core2Duo as my proc. Someone in IRC told me that the i386 was the correct version I should use, right after I installed ubuntu it is saying that my version is unsupported by almost 100% of the programs I tried to install.

Is anyone else getting this? Is it just momentary?

Thanks

> Amarok cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
> xchat:
 Depends: tcl8.4 (>=8.4.5) but it is not installable


---

### Post by Dr Small on 2007-10-18
Please go to "Thread Tools" and click "Mark as Solved", so other know that your problem is solved :D

---

### Post by xealous on 2007-10-18
i also have this issue and couldn't solve it. i've almost checked all the boxes but still cannot update and install programmes..

---

### Post by gonxo.85 on 2007-10-18
[B]EDIT: It's almost explained at the first post. Just to clarify.
If checking some of them at Software Sources doesn't work for you. Try changing the server from were you are downloading, by defaut I had the server called main but I changed if for one server at spain and it worked.
You should find this at Software Sources too.
[/B]

I have just installed ubuntu 7.10 and I have the same problem.

Can someone point a solution?

---

### Post by gali98 on 2007-10-18
I am also having the same problem... your explanation is kind of cryptic... What exactly do we do? thanks...
Kory

---

### Post by bruce89 on 2007-10-18
> **xealous said:**
> i also have this issue and couldn't solve it. i've almost checked all the boxes but still cannot update and install programmes..

> **gonxo.85 said:**
> I have just installed ubuntu 7.10 and I have the same problem.

Can someone point a solution?

> **gali98 said:**
> I am also having the same problem... your explanation is kind of cryptic... What exactly do we do? thanks...
Kory

sigh...

[QUOTE=mitchbones]EDIT:I have solved the problem. For anyone else with my misfortunes, go to System>Software Sources> and I turned checked some of them.[/QUOTE]

---

### Post by mitchbones on 2007-10-18
I checked all of them on the ubuntu tab, only the first (not source) on the third-party tab.

---

### Post by mitchbones on 2007-10-18
The problem is not offically solved. When trying to install music codecs I ran into the same error

> Xine extra plugins cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by gali98 on 2007-10-18
> **gonxo.85 said:**
> [B]EDIT: It's almost explained at the first post. Just to clarify.
If checking some of them at Software Sources doesn't work for you. Try changing the server from were you are downloading, by defaut I had the server called main but I changed if for one server at spain and it worked.
You should find this at Software Sources too.
[/B]

I have just installed ubuntu 7.10 and I have the same problem.

Can someone point a solution?

Thanks...

---

### Post by repustech on 2007-10-19
> Originally Posted by gonxo.85  View Post
I have just installed ubuntu 7.10 and I have the same problem.

Can someone point a solution?

I found a method that worked for me... I can now watch dvd's in Totem Xine Backend.

It looks like 7.10 does not use the package "xine extra plugins" and will not let you install it. They have renamed the packages and you can install them through synaptic. Install the following and it should work with Totem Xine Backend.

libxine1-ffmpeg
libxine1-gnome
libxine1-plugins

if trying to play dvd's, you will need these too.

libdvdcss2
libdvdnav4
libdvdread3

Hope that helps... :)

---

### Post by StratusX on 2007-10-19
Under the first 2 tabs in Software Sources, Ubuntu Software and Third-Party software, check all the boxes other each, close and reload.

That's what worked for me, atleast.

Hope that helps!

---

### Post by gali98 on 2007-10-20
Okay I have not seen any other problem like this... Whenever I try to update my sources (I'm on feisty) The "Translation-en_US" always fails. So I can't update anything. And I get the same (i386 can't install) error. Is anybody else having this problem? Any ideas?
Kory
EDIT: Never Mind... I fixed everything

---

### Post by gonon on 2007-11-02
well if you solved everything mind sharing with others what exactly did you do to have it working .thanks

---

### Post by clparker on 2007-11-12
seems to be a problem w/ the add/remove app, try synaptec instead.

---

### Post by ABE3K on 2008-02-21
> **mitchbones said:**
> The problem is not offically solved. When trying to install music codecs I ran into the same error

I know this reply is a bit late but I think it might help someone out there :)
I had the same problem where somehow I was unable to install the xine extra plugins simply from the add/remove page nor from the synaptic manager even after checking the suggested solution 
downloading the extra codecs auto installer from one of the mirrors from the link below solved the problem for me

[http://packages.ubuntu.com/feisty/all/libxine-extracodecs/download]("http://packages.ubuntu.com/feisty/all/libxine-extracodecs/download")

---

### Post by thestig_992 on 2008-03-16
I just had that same problem with installing amarok, and i found that under add/remove prgrams -> preferences there are some boxes unticked in the first tab. Turn them on and you should be fine

---

