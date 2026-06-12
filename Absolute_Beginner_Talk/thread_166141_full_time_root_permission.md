---
title: "full time root permission?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-04-25
Hi, i'm new to ubuntu and i'm wondering if there is a way to log in a root and have full permissions all the time? or is there a way i can give root powers to a user?

Thanks much

---

### Post by Sef on 2006-04-25
> Hi, i'm new to ubuntu and i'm wondering if there is a way to log in a root and have full permissions all the time? or is there a way i can give root powers to a user?

You don't want to do that.  If you do that, you are creating the same problem as with Microsoft.  If something gets in, it could go anywhere in your system and then you would have the problems with viruses, worms, trojans, etc.

Use sudo if you need to download something.  It is much safer than using root.

Read this on 'Root Sudo'.  Here are the benefits and a link.

> Benefits of using sudo

The benefits of leaving root disabled by default include the following:

    *

      The installer has to ask fewer questions
    *

      Users don't have to remember an extra password, which they are likely to forget
    *

      It avoids the "I can do anything" interactive login by default -you will be prompted for a password before major changes can happen, which should make you think about the consequences of what you are doing.
    *

      Sudo adds a log entry of the command(s) run (In /var/log/auth.log). If you mess up, you can always go back and see what commands were run. It is also nice for auditing.
    *

      Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are.
    *

      Allows easy transfer for admin rights, in a short term or long term period, by adding and removing users from groups, while not compromising the root account.
    *

      sudo can be setup with a much more fine-grained security policy


[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo")

---

### Post by mjm115 on 2006-04-25
One of the reasons Windows is so vunerable is because it gives the user full administrative (root) permissions.  This is a mistake Ubuntu does not make.

By default the user created during the installation is added to the admin group (sort of like a Power User in Windows).  This user can perform root tasks by going to a terminal and sudo <command>.

---

### Post by cptjaben on 2006-04-25
ahh i see, that's good to know.

my problem then is that when i try to acess my fat32 hardrive partition i can't write to it because it says i don't have permission, how do i get permission to write to it?

thanks

---

### Post by aysiu on 2006-04-25
[QUOTE=cptjaben]ahh i see, that's good to know.

my problem then is that when i try to acess my fat32 hardrive partition i can't write to it because it says i don't have permission, how do i get permission to write to it?

thanks[/QUOTE] [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

