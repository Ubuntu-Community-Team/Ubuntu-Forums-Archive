---
title: "Help me please!"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by jbennet on 2006-03-10
Ok, how do I add KDE ato edubuntu?

Secondly, the OS is for use by people who may potentially harm the system so how can i make it so you must enter the root password instead of your own to run system utilities?

---

### Post by Pragmatist on 2006-03-11
1. installing KDE: in a terminal try this: ```
sudo synaptic
``` then use synaptic's search feature to find KDE and install it.

2. Root access:  Read this first:
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

---

### Post by aysiu on 2006-03-11
If you know how to use the terminal, type this: ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` that'll add the Kubuntu KDE with its accompanying packages. You could also try: ```
sudo apt-get update
sudo apt-get install kde
``` which will add the standard KDE with its accompanying packages or ```
sudo apt-get update
sudo apt-get install kde-core
``` which will install only the basic KDE.

---

