---
title: "fairly new linux user, 2 questions"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by kenailes on 2006-01-31
Okay, so think i am getting this thing figured out to the point where my windows partition gets smaller every day. I have a couple of questions that I am having a hard time with though:

1.  for some idiotic reason when i created my partitions i didn't create a swap partition.  i have 4 partitions on my hard drive:

1. windows
2.  linux
3. WINDOWS SWAP
4. media

is it possible to somehow use my windows swap partition as my linux partition as well?  if so, how and if not, how can i create that swap partition after the fact and tell breezy to use it?  i mean i am assuming i can use gparted to do it, but the what?

2.  like an idiont (detect a thread here??) i used windows partition commander to partition my hard drive before installing ubuntu.  now that i have done it, i can't uninstall system commander because it tells me that if i do, i won't be able to access any of the partitions i created.  i am really trying to keep from having to back everything up, delete all of my partitions execpt for my windows partition and starting again.  any pros out there can tell me how to uninstall partiiton commander without having to start from scratch?

thanks for your help

---

### Post by morphodone on 2006-01-31
what filesystem did you use to create the linux partition?

i cannot think of a reason why uninstalling a program in windows would make your linux parition unusable.

how did you tell windows to use a swap partition?  i'm not asking to learn about windows - i've just never seen anyone do this before...i didn't know that was possible.

---

### Post by mstlyevil on 2006-01-31
[QUOTE=kenailes]Okay, so think i am getting this thing figured out to the point where my windows partition gets smaller every day. I have a couple of questions that I am having a hard time with though:

1.  for some idiotic reason when i created my partitions i didn't create a swap partition.  i have 4 partitions on my hard drive:

1. windows
2.  linux
3. WINDOWS SWAP
4. media

is it possible to somehow use my windows swap partition as my linux partition as well?  if so, how and if not, how can i create that swap partition after the fact and tell breezy to use it?  i mean i am assuming i can use gparted to do it, but the what?

2.  like an idiont (detect a thread here??) i used windows partition commander to partition my hard drive before installing ubuntu.  now that i have done it, i can't uninstall system commander because it tells me that if i do, i won't be able to access any of the partitions i created.  i am really trying to keep from having to back everything up, delete all of my partitions execpt for my windows partition and starting again.  any pros out there can tell me how to uninstall partiiton commander without having to start from scratch?

thanks for your help[/QUOTE]

You should be able to boot into windows and move your swap to the same partition as Windows. Then you would be able to reformat the old swap partition for linux. Honestly, I would just reinstall Ubuntu and let it take the free space you install it on and partition it for you. It will give you a swap partition by default on install. That would be the easiest way IMHO.

---

### Post by mstlyevil on 2006-01-31
[QUOTE=morphodone]what filesystem did you use to create the linux partition?

i cannot think of a reason why uninstalling a program in windows would make your linux parition unusable.

how did you tell windows to use a swap partition?  i'm not asking to learn about windows - i've just never seen anyone do this before...i didn't know that was possible.[/QUOTE]

You can do it after you install Windows as long as you create a second partition for it upon install. I don't do it that way because Windows runs better when the swap file is on the same partition.

---

### Post by morphodone on 2006-01-31
[QUOTE=mstlyevil]You can do it after you install Windows as long as you create a second partition for it upon install. I don't do it that way because Windows runs better when the swap file is on the same partition.[/QUOTE]

Well, that's something I'll never get to try...I honestly can't stand to boot into windows anymore.

gnu/linux has spoiled me!

[QUOTE=mstlyevil]Honestly, I would just reinstall Ubuntu and let it take the free space you install it on and partition it for you. It will give you a swap partition by default on install. That would be the easiest way IMHO.[/QUOTE]

I completely agree.

---

