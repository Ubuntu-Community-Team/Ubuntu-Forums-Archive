---
title: "Need Help Installing Program (Mailscanner)"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-10-31
I installed the gutsy gibbon upgrade from feisty, and Mailscanner failed. now I cannot uninstall, install, reinstall, update, remove, all fail saying there is an error and I need to do something manually what I don't know. I need to know which file from the mailscanner site to download and how to install it. They have a dibian file but it is older the the version on synaptic manager and will not install because its older. I also have not installed any programs - packages like tar or deb so I don't know how to do this type of install. anyone want to guide dog me through this.

---

### Post by amingv on 2007-11-02
Hi

Can you tell us what does the error message say?

Also may be worth trying:

```
sudo apt-get autoclean
```

and

```
sudo apt-get autoremove
```

If you wish to learn to install/manage many packages in Ubuntu/Kubuntu, 
[>>this guide]("http://monkeyblog.org/ubuntu/installing/") may help you. It did a lot for me  when I learned to install packages in Kubuntu.

Please let me know the outcome of my suggestion.

---

