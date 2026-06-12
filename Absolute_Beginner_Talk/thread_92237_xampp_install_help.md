---
title: "xampp install help"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by thenoobest1 on 2005-11-19
[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377) i followed this tutorial letter for letter (i just now changed the file name to xampp.tar.gz instead of the xampp-linux-1.5.0.tar.gz because it was a pain to keep typing out, i got the same response though) and i get this...  

"you may not specify more than one '-acdtrux' optoin"

what am i doing wrong?

i tried this too 
tar xfvz xampp.tar.gz /opt but i get "invalid option -a"

it will extract though if i use "tar xfvz xampp.tar.gz" or even just "tar xampp.tar.gz"

any help is appreciated

---

### Post by thenoobest1 on 2005-11-19
fixed my own problem... i didnt realise that everything was case sensitive in the terminal:???:

i do have another problem though, when i try to start xampp it says theres another daemon running... im guessing ubuntu has the server running... so basically how do i turn it off?

---

### Post by matthewv on 2005-11-19
btw... you don't need to keep typing it out everytime. Linux has auto completion in the terminal: press tab while typing and the filename, if it is the only one that exists that starts how you have started, will be completed for you: e.g
```

tar xvfz xam<tab><enter>

```

EDIT: In regards to your question, maybe uninstalling apache2 or apache, or something like that

---

### Post by thenoobest1 on 2005-11-19
thanks for the shortcut, ive removed all the apache and mysql servers through synaptic and it starts. i cant log in yet, but thats a xampp problem, i just have to find the default user and password i think. thanks for the help.

---

### Post by hardclip on 2005-11-19
Default user name is root..

Just hit enter for password..

You can find this in the readme file

---

