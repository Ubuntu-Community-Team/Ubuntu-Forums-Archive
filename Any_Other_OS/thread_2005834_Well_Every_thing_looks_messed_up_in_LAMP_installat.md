---
title: "Well Every thing looks messed up in LAMP installation !!"
date: 2012-06-18
forum: Any Other OS
---

### Post by abhiionweb on 2012-06-18
I installed LAMP manually using the various components through the ".tar.gz" packages available online on my Linux mint 13 cinnamon editon....but after everything ( apache2.4.2 was working , mysql was working ) the lone thing that was left to check was PHP5 ...i made a test.php file to check the configurations of php but insteas it showed me my own code <?php phpinfo(); ?> .........out of this frustration i asked for help online and various people suggested me [help.ubuntu.com/community/ApacheMySQLPHP](help.ubuntu.com/community/ApacheMySQLPHP) and i used tasksel to install my LAMP components again (without removing the previous installation).....but after following everything the problem seems to persist ....now my apache is working but when i point it to show my localhost/test.php it gives me a 404 not found.....  

Probably i would ask people here to either assist me in combating this issue or either tell me how to uninstall the components installed by both manual installation and tasksel and make new start again in installing these components ....

Thanks in advance !!!

---

### Post by sandyd on 2012-06-18
> **abhiionweb said:**
> I installed LAMP manually using the various components through the ".tar.gz" packages available online on my Linux mint 13 cinnamon editon....but after everything ( apache2.4.2 was working , mysql was working ) the lone thing that was left to check was PHP5 ...i made a test.php file to check the configurations of php but insteas it showed me my own code <?php phpinfo(); ?> .........out of this frustration i asked for help online and various people suggested me [help.ubuntu.com/community/ApacheMySQLPHP](help.ubuntu.com/community/ApacheMySQLPHP) and i used tasksel to install my LAMP components again (without removing the previous installation).....but after following everything the problem seems to persist ....now my apache is working but when i point it to show my localhost/test.php it gives me a 404 not found.....  

Probably i would ask people here to either assist me in combating this issue or either tell me how to uninstall the components installed by both manual installation and tasksel and make new start again in installing these components ....

Thanks in advance !!!
So you compiled from source?
If you compile from source, there are a few problems:
[LIST=1]
[*]Doesn't work with stuff like tasksel
[*]Instructions in the wiki are incompatible
[*]No automatic updates
[*]Not compatible with packages in the repository
[/LIST]

So what components did you install - we cannot tell you how to remove them if we do not know which ones they are.

---

### Post by Perfect Storm on 2012-06-18
Moved to Other OS/Distro Talk.

---

