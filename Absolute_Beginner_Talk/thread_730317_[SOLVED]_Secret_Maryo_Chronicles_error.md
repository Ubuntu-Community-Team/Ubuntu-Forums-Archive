---
title: "[SOLVED] Secret Maryo Chronicles error?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-03-20
Ive installed secret maryo chronicles from synaptic but i coulnt find it in the applications menu in ubuntu so i ran "smc" from the terminal and i get this error output

```
carl@carl-desktop:~$ smc
CEGUI::Exception: DynamicModule::DynamicModule - Failed to load module 'libCEGUIDevILImageCodec.so': libCEGUIDevILImageCodec.so: cannot open shared object file: No such file or directory
CEGUI Exception occurred : DynamicModule::DynamicModule - Failed to load module 'libCEGUIDevILImageCodec.so': libCEGUIDevILImageCodec.so: cannot open shared object file: No such file or directorycarl@carl-desktop:~$ 

```

Can anyone tell me what this means and what i need to do in an idiots guide way :lolflag:

---

### Post by kamitsukai on 2008-03-20
Fixed the problem looks like the dependacy is broken in gutsy theres already been a bug report filed [here]("https://bugs.launchpad.net/ubuntu/+source/smc/+bug/118308") it appears from the comments that to solve the issue you have to manualy install "libcegui-mk2-dev" (without the quotes) from synaptic

---

