---
title: "VLC and Samba on Gutsy without mounting"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by rondin on 2008-04-07
This is very strange and I cannot understand why it happens.

I know that Vlc is not able to browse samba shares but it has an SMB Access module and it's able to play files through smb://

It works perfect if I run the command through the console

```
# vlc "smb://<Sharename>/<Sharefolder>/myvideo.avi"
```

But the problem is when I browse, right click on the file and Open with Vlc or when I drug my file from the browser to Vlc window. Vlc opens but it doesn't run the file. It worked fine on Hardy but on Gutsy I am not able to make it work. There is nothing on /var/log/messages so I cannot really debug or find out what is causing it. I have tried to run Vlc through console, I have noticed that when I go to Open File (Ctrl +F ) works but Quick Open File (Ctrl +O) doesn't. And If I try it two times I get the following error:

(.:16301): Gtk-CRITICAL **: gtk_tree_model_get: assertion `GTK_IS_TREE_MODEL (tree_model)' failed
Segmentation fault (core dumped)

I am not sure if this has anything to do or it's related to that issue. I was wondering if there is any way that I can find out the problem or at least debug and find out what happens when I do right click.

---

### Post by rondin on 2008-04-07
I was wondering if somebody can move this thread to: Main Support Categories -> Multimedia & Video. I think it suits better there.

---

