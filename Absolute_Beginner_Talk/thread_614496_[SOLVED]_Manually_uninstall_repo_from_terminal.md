---
title: "[SOLVED] Manually uninstall repo from terminal?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by TidusBlade on 2007-11-16
I by mistake installed a repo I shouldn't have and now my Adept Manager returns 
```
The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.
```
apt-setup dosent do anything and apt-get-setup returns 
```
watermelon@Omega:~$ apt-get update
E: Type 'http://ppa.dogfood.launchpad.net/amaranth/ubuntu' is not known on line 57 in source list /etc/apt/sources.list
```
So I guessed I have to remove the repo, but I cant go into the Adept Manager, so anybody knows how to do it from the terminal?
Thanks ;)
EDIT: Im using Kubuntu Gutsy.

---

### Post by scorp123 on 2007-11-16
> **TidusBlade said:**
>  so anybody knows how to do it from the terminal?  You use Kubuntu? So you have KDE as desktop? Log in to your KDE session, open "konsole" (KDE's terminal application), and then type this: ```
sudo kate /etc/apt/sources.list
``` ... When it asks for a password, it would normally be your own. When the editor opens remove the offending line, but leave all the others untouched. Then just go to the menu "File > Save" to save your file, and then exit. At last you execute this so that the changed repos take effect: ```
sudo apt-get update
```

---

### Post by TidusBlade on 2007-11-16
Thanks alot :) Everything worked perfectly ^^

---

