---
title: "Error installing Pidgin"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by gentix on 2007-09-22
So, I decided I need Pidgin instead of Gaim.  Gaim is great, but Pidgin sounds really cool -- especially with Google Talk, etc.

I downloaded Pidgin 2.2.0 from getdeb.net, but when I tried to open the file, I gen an error on the "Package Installer"

I read somewhere I ought to uninstall Gaim first, so I removed everything Gaim-related using the Synaptic Package Manager (the add/remove programs function wouldn't work because of something to do with packages).  That went fine, I restarted, and Gaim appeared unchecked in the add/remove packages manager.  So far so good. 

I tried to open the file from getdeb again, but I get (I think) the same error: Error: Dependency is not Satisfiable: pidgin-data.  Does anyone know how to resolve this problem?

---

### Post by alienexplorers on 2007-09-22
What is the exact error message and when does it occure, when you are doing a ./configure, make..etc.

---

### Post by gentix on 2007-09-22
The exact message is 
> Error: Dependency is not Satisfiable: pidgin-data

It happens when I click "open" on the FireFox dowload manager.  It appears on the "Package Installer".

---

### Post by alienexplorers on 2007-09-22
Try looking at this page
> [http://ubuntuforums.org/showthread.php?t=474071](http://ubuntuforums.org/showthread.php?t=474071)

---

### Post by Sturmeh on 2007-09-22
Be sure to check pidgin actually doesn't work to start with.

Originally I got lots of errors, but it worked fine. :\

---

### Post by mcduck on 2007-09-23
When you download Pidgin from Getdeb you need to get both packages, pidgin and pidgin-data. After you've downloaded you need to install them both at the same time as they depend on each other. If you downloaded them to your desktop this command will install them (Actually all .deb packages on desktop):
```

sudo dpkg -i ~/Desktop/*.deb
```

---

### Post by Titi on 2007-09-23
just want to note that gaim supports google talk as well. but not the actual talking (with a microphone). but i don't think that's supported by pidgin either.

---

### Post by mcduck on 2007-09-23
> **Titi said:**
> just want to note that gaim supports google talk as well. but not the actual talking (with a microphone). but i don't think that's supported by pidgin either.

They are the same program, Gaim is just older version. The project had to change their name because AOL didn't like them having the 'aim' in the name.

---

