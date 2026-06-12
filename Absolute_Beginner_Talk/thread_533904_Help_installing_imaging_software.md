---
title: "Help installing imaging software"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Shinjijon on 2007-08-24
I wasn't really sure who to ask for help on this, but I thought I might try here.  I installed Ubuntu for the ease of installation, but I am having trouble getting the program to run that I want.  It is called IVE (or Priism4) and can be found at [http://www.msg.ucsf.edu/IVE/](http://www.msg.ucsf.edu/IVE/).  I followed their installation instructions which include extracting the tarball and running a ./post_setup.sh.  But when their installation instructions have me running ./Priism_setup.sh (which is a file in the directory) I get an error saying "command not found".  I'm new to Linux and I'm kind of at a loss as to why this is happening.  I've emailed the makers of the program, but I am also wondering if this is because of the lack of access to the root account.

Any help in this would be very much appreciated.

~Jonathan

---

### Post by Golyadkin on 2007-08-24
You can put "sudo" in front of commands to run them as root. Also, try running "chmod +x Priism_setup.sh" to make the script executable.

---

### Post by Shinjijon on 2007-08-24
hmm, didn't work.  But anyways I ran into this line in their documentation.

"Before starting Priism, an X server must be running and the DISPLAY environment variable must be set appropriately so clients can connect the server (setting the DISPLAY to :0.0 is generally appropriate for clients connecting to an X server running on the same machine)."

Any idea as to what that means?

~Jonathan

---

