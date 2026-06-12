---
title: "programming setting file permissions"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-04-22
I am trying to save my very basic c++ programs in emacs and am experiancing difficulties.:-# 
It it saying that I don't have permission to save the file there or even do a mkdir.
As far as I know I am logged in with the highest level of authorita. I have checked the user / group section and have all permissions enabled. Can anyone help?
 By the way I am trying to do a mkdir in the /usr/local dir.:-k

---

### Post by unbuntu on 2006-04-22
Try saving it under your home directory ~

---

### Post by IYY on 2006-04-22
> As far as I know I am logged in with the highest level of authorita. I have checked the user / group section and have all permissions enabled. Can anyone help?

The highest level of authority belongs to root. You are just logged in as a user who can run commands as root using the sudo command. If you want a root shell, you could run something like

sudo bash

---

