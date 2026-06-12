---
title: "sudo window themes not same as users"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-08-29
Launching Synaptic Package Manager via System->Admin, I have very square buttons and a basic ok/cancel buttons. When it looks normal here :-
[https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=RepositoriesUbuntu03.png](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=RepositoriesUbuntu03.png)

Other example is gedit, lauched via a term noramlly "gedit" it looks good, but lunched with sudo "sudo gedit" it looks more basic!?!

---

### Post by mcduck on 2006-08-29
That is because they run as root, not as your own user. But there is a simple trick that makes root always have same theme and icons that you have. Just run these commands in a terminal:
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by Bachstelze on 2006-08-29
Also, remember to always use gksudo insteald of sudo to run GUI apps as root.

---

### Post by IanVaughan on 2006-08-29
Worked a treat, cheers!

> **HymnToLife said:**
> Also, remember to always use gksudo insteald of sudo to run GUI apps as root.

Ok, but 2 things, 1 lunching from menu items, cant use gksudo, but your last post fixed my GUI.
2. ALL user guides state running sudo, so I normally just copy and paste!

---

### Post by n8bounds on 2006-08-29
> **mcduck said:**
> That is because they run as root, not as your own user. But there is a simple trick that makes root always have same theme and icons that you have. Just run these commands in a terminal:
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

You are so awesome for sharing that

---

### Post by Toxicity999 on 2006-08-30
sudo gedit is just a non in your face way guides use... I mean when cut and past a ton of lines in one block to have them processed most users don't want the gksu prompt and just using command sudo seems more fluid. It's all perspective I suppose. It's all good anywho as far as I know. You might find using nano more convenient for those small config file changes to avoid those few seconds waiting for gedit which seems for ever when you're itching to dive into those config files! lol.

---

