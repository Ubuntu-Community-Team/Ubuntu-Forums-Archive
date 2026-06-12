---
title: "adept manager"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by lancyyy on 2008-01-22
hey can someone plz help me 
my adept manager doest open anymore because somewhere in setup third.... somthing 
i typed a ftp but it was only for http and now when i try to open adept it says:
the APT database could not be opend! this may be caused by incorrect APT configuration or some similar problem. try running apt-setup and apt-get update in terminal and see if this helps to resolve the problem.
so thats what i do and i get this:

nickolas@laptop:~$ apt-setup

bash: apt-setup: command not found

nickolas@laptop:~$ apt-get update

E: Type 'ftp://ftp.funet.fi/pub/gnu/funet' op regel 85 in bronlijst /etc/apt/sources.list is onbekend

can someone help me ? 
grtz:)

---

### Post by emarkd on 2008-01-22
apt doesn't support that ftp address you've got in there.  Type:
```

sudo gedit /etc/apt/sources.list
```

and when the editor opens, remove the ftp line from the file.  Save it and then

```
sudo apt-get update
```

and everything should be fine again.

---

### Post by fatality_uk on 2008-01-22
Are you meaning "apt-get install <prgram name>"?
If you type apt-man from a terminal, you will get a useful manual which list options for using the advanced package tool.

---

