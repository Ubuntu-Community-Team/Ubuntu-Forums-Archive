---
title: "So many groups"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-02-03
There are so many groups in Ubuntu and when I create a user, it also creates a group. Can I avoid this. I mean can I delete groups which do not have users.
Which groups should I keep?

---

### Post by szymon_g on 2008-02-03
some people say that's the easiest /and dirty/ way for deleting a group is deleting it's description in /etc/group file....
but, than again, it's a bit dirty way.....


and some other people say thats groupdel is usefull for it ;p

---

### Post by Delkster on 2008-02-03
What kinds of groups do you mean? If there are groups that you have created (or that have been created with new users you have added), and you know that they are no longer used, it's safe to delete them.

If you mean the large number of groups that have been there from the start, with names such as adm, cdrom, video, plugdev, gdm etc., they're generally there for a purpose. They may be used by system services or other such purposes that are not immediately obvious. You probably shouldn't delete them unless you know what you're doing.

Generally, groups with an id number lower than 1000 are system groups used by various services and other such purposes, and probably should not be deleted. Groups with an id higher than 1000 are generally groups created when you add a new user or just manually add a new group without explicitly specifying the id for the new group.

---

### Post by jesrani on 2008-02-03
> **Delkster said:**
> What kinds of groups do you mean? If there are groups that you have created (or that have been created with new users you have added), and you know that they are no longer used, it's safe to delete them.

If you mean the large number of groups that have been there from the start, with names such as adm, cdrom, video, plugdev, gdm etc., they're generally there for a purpose. They may be used by system services or other such purposes that are not immediately obvious. You probably shouldn't delete them unless you know what you're doing.

Generally, groups with an id number lower than 1000 are system groups used by various services and other such purposes, and probably should not be deleted. Groups with an id higher than 1000 are generally groups created when you add a new user or just manually add a new group without explicitly specifying the id for the new group.

There are lot of groups created when I installed the system and new groups seem to be getting created with each software install. I checked that those created automatically have an ID<1000 and the user that I created during install made a group with ID = 1000. Can I delete this group? Groups after that have an ID>1000 so I will delete what I dont need. But is it not confusing to keep getting so many groups created. I am not able to see the logic to this. Is there any where I can get a better understanding.

---

### Post by jflarm on 2008-02-03
Since Linux and Unix are ALL about security, it makes sense to have some programs create their own user and group. Then the permissions will be set for those.
Normal users will have their own group also, for example: user1 will have a primary group of user1, then you can add this user1 to the other groups created in the /etc/group file.
Hope this helps, but if you want to know more, just study the system services, that way you'll know what each user and group is used for.

---

