---
title: "restore my admin privilege"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by day9981 on 2007-05-19
Hi,

    I  installed Ubuntu on my laptop days ago, I have to say it is great. However, I am a newbie to Linux. There is only one user on my machine, i.e. by default the administrator. But when i played around, I unchecked the admin privilege of this id in the user and group management, which results in that i now have no administrator privilege to access some settings i made before. And also I want to move a deleted file back from the trash but failed. Anyway to restore my admin privilege? Thanks.

---

### Post by bobplano on 2007-05-19
you can go into recovery mode and put yourself back in the admin group. i think the file to edit is something like group. or you can go to users and groups under system>administration, the groups tab in the windows and add yourself to the users under admin

---

### Post by taurus on 2007-05-19
Yes, it's /etc/group and you need to belong to _both_ adm and admin before you can use sudo/gksudo.

```
nano -B /etc/group
```

<Ctrl>o to save and <Ctrl>x to edit.

---

### Post by mahiyar on 2007-05-19
So the path is set for you
1)Go to the recovery console mode.
2)From the CLI there edit *group *file using >>nano -B /etc/group
3)In this file add yourself to the admin group

If  you do know how to modify the file or what line to put or where to put do not worry. You may use this instead

1)Go to recovery mode (When in grub, when the timer is counting down 3 secs press Esc)
2)Once in recovery CLI enter these lines
        >>addgroup *yourusername *admin
        >>addgroup *yourusername *adm
3)Restart >>shutdown -r now

*yourusername *is the name from whom you snatched the admin privileges.

And I guess you would be back in business.

---

### Post by day9981 on 2007-05-21
Got it. Thank you very much. :-)

---

