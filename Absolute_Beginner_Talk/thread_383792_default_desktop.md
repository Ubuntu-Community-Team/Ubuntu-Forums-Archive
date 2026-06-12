---
title: "default desktop"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-03-13
Messing around with my desktop I've ended up with no bar at the bottom and no applications menu at the top. (xubuntu) I added the xfce Menu top right which I think does much the same as the apps. menu but I feel I should be able to get back to where I started but can't. Any ideas please? ie. default settings.

---

### Post by annda on 2007-03-13
i'm not using Xfce at the moment, but all desktop managers should be the same:

do you have a .Xfce file (or something similar) in your home directory? delete the file and restart X. default settings should be re-created.

---

### Post by heatrag on 2007-03-13
I've got to the working directory* home *then
ls -a 
. .. *richard*

Is it me?

---

### Post by heatrag on 2007-03-13
or maybe this is a help?
richard@heatrag:~$ ls -a
.                 .config      .gtk-bookmarks    .recently-used
..                Desktop      .gxine            .sudo_as_admin_successful
.AbiSuite         .dmrc        .ICEauthority     .thumbnails
.aspell.en.prepl  .gconf       .lesshst          tt.doc
.aspell.en.pws    .gconfd      .local            .Xauthority
.bash_history     .gimp-2.2    .mailcap          .xine
.bash_logout      .gksu.lock   .mozilla          .xsession-errors
.bash_profile     .gnome2      Office_documents
.bashrc           .gnumericrc  .openoffice.org2
.cache            .gqview      .realplayerrc

---

