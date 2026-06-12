---
title: "[SOLVED] Problems installing application with .RUN extension in Ubuntu 7.10"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-12-14
I downloaded a file that ends with a .RUN extension and I can't get it to work properly using Ubuntu 7.10:

I started with the instructions listed at:

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

Here's the problem: 

I double-click on the .RUN file, I choose "Run  in Terminal" - the application starts running and then prompts me with the message "You need to run this installer as the super-user." and then quits.

So I launched terminal, and tried:

sudo application.run 

and I get the error message "command not found.

I even tried "SU" and then attempted the run the file and that also results in .RUN not workinig

---

### Post by Hospadar on 2007-12-14
Hi, I believe you'll need to do something like "sudo sh application.run" and if that doesn't work, try doing a "chmod a+x application.run" to add execute privileges to the file.

Hope this helps!

---

### Post by vortex0007 on 2007-12-14
Thank you. The command you supplied worked.

---

