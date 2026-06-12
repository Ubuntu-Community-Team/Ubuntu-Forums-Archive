---
title: "ndiswrapper problems"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by cinmachina on 2007-07-03
Hello guys! Fist and foremost I want to thank the users of this website for always answering my questions in a timely and useful manner.

That being said, here is my question:

I have a problem with my ndiswrapper. Everytime I restart my laptop, it won't pick up my wireless connection unless I push Function + F2 (The switch to toggle my wireless receiver) off and on again. Is there a way to make it so I don't have to do this? It's a huge annoyance for me!

Thanks!

---

### Post by egonkasper on 2007-07-04
I also have the same problem *sometimes*.   What type of wireless card do you have?

---

### Post by hoscha on 2007-07-04
i cant even get ndiswrapper installed....what are the commands for doing that....i have in unzip on my desktop

---

### Post by jspangler on 2007-07-04
> **hoscha said:**
> i cant even get ndiswrapper installed....what are the commands for doing that....i have in unzip on my desktop

It's much easier to install ndiswrapper through Synaptic Package Manager.

1. Go to System/Administration/Synaptic Package Manager (and type in your password)
2. Type in "ndis" and click on the boxes for "ndisgtk" and "ndiswrapper-utils-1.9". In each box click "Mark for Installation" It might tell you that you also have to install other files. That is "OK"
3. Click "Apply" to finish the installation.
4. Open a terminal window and type:

[PHP]sudo ndisgtk[/PHP]

Enter your password.

5. Choose the windows driver you have for your wireless driver. I have found that I sometimes have to reboot now.

6. See if your wireless network is working!

---

