---
title: "Prompt... What Next?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by JTeagle on 2007-07-15
I have been introduced to VMware and a Ubuntu [allegedly] pre-prepared server installation ("it's the next best thing since sliced bread"... isn't it always? {:v)  ).

I've got the Ubuntu VM running, and I'm logged in, but I'm basically at the prompt all dressed up and nowhere to go. Is it not possible to get a graphical UI on the server version? I had (perhaps stupidly) assumed server = desktop + everything server-like on top. If you can get a GUI, can someone please tell me how to install and / or start it before I get a headache from banging my head against the wall? {:v)

Assume I'm a Linux command-line newbie (because I am - I always thought ll was the *nix equivalent of Windows' dir but bash says it doesn't know what ll is... not very encouraging!)

Thank you!

---

### Post by christhemonkey on 2007-07-15
ls i *NIX equivalent of dir.

The server edition does *not* include a graphical environment no. (as on a server this would probably be a waste of resources!)

You can install a graphical environment easily though just type:
```
sudo apt-get update 
```
and then if that completes ok:
```
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop 
```

---

### Post by Wim Sturkenboom on 2007-07-15
> 
server = desktop + everything server-like on top
nearly correct: :)
server = desktop + everything server-like on top - **everything not strictly required for a server**
So no GUI and a whole list of other stuff

---

