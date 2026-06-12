---
title: "[SOLVED] can't download any software"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by SurlyDune on 2008-04-02
when i try to install anything including restricted drivers packages or programs i get the message "the list of applications is not availabe Click 'Reload' to load is. to reload the list you need a working internet connection" (yes available is spelled wrong too, and yes i have a working internet connection). So i click refresh (cuz reload isn't an option) and it goes to a screen that shows it downloading 6 of 6 files but does nothing to my ability to download anything. I also tried installing automatix from the internet but when i try to install it from my desktop i get the message "Error; Dependency is not satisfiable: tango-icon-theme-common" these problems are becoming pretty irritating and any help i could get would be awesome.

---

### Post by kestrel1 on 2008-04-02
Have you gone to System / Administration / Software Sources & checked what is ticked in each section?

---

### Post by taavikko on 2008-04-02
You propably have the repos commented out ...
open synaptic ->Settings->Software sources
put a tick on: Main, Universe, Restricted, Multiverse 
remove tick from cd-rom
and get from server: Main server

and exit, update synaptic

---

### Post by Kevbert on 2008-04-02
You need to set up your Software Sources - under Preferences - Administration - Software Sources.  Under Ubuntu Tab select first four sources and select a server if necessary.  You may find you need to download a few updates...

---

