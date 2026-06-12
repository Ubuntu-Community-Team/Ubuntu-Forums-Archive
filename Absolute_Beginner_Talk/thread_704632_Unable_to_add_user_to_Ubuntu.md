---
title: "Unable to add user to Ubuntu"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-02-22
A strange phenomenon has occurred.
2 weeks ago I added a user name
'rajah'

When I was absent from the room he would log into that account and surf the net using firefox.
Yesterday he said that when he logged in, firefox window briefly appeared and then vanished.

Using
system/administration/users and groups

I gave him more and more permissions, but still the firefox window opened before vanishing again.

Then I had the idea of deleting rajah and recreating the account.

Again I go to
system/administration/users and groups
then
'add user'

but now rajah is not appearing in the list of users.

The same thing has happened with another friend for whom I created an account.

As a relative beginner, I find I am totally stumped.

Regards

John

---

### Post by Crooksey on 2008-02-22
Try using the adduser command instead....

```

$ sudo adduser -m <user>
```

---

### Post by radiocognition on 2008-02-22
Quick question, when you say that the user would log onto your computer while you were out of the room, do you mean that the user was physically at your computer or using a remote desktop client like VNC.  It is possible for a user to log into your machine remotely through VNC, and I am not sure how stable that is.

---

### Post by Andavane on 2008-02-23
> **Crooksey said:**
> Try using the adduser command instead....

```

$ sudo adduser -m <user>
```

Crooksey: When I do that I get the message [sic]

The group 'rajah' already exists.

But when I go to see my users in 'user settings' his name is not there.

However, when I go to 'group settings' there is a fairly lengthy list of names and 'rajah' is within that list.
Am not sure how to proceed.
~ ~ ~ ~
The answer to your quick query, radiocognition, is that 'rajah' is my carer as I use a wheelchair. When he takes me to the bathroom he uses my linux box, but I want him to be using it separately, so yes he is physically at my screen.

Thank you all for your help.

Regards

John

---

### Post by zvacet on 2008-02-23
```
sudo adduser rajah
```

To add user to group 

```
sudo adduser rajah rajah
```

Or you can look [here.](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by Andavane on 2008-02-24
Ok I am trying to grapple with this.

sudo adduser rajah rajah
 tells me that the group rajah already exists.
So my next idea was to delete rajah from the group.
When I go to delete the group rajah I get:

Are you sure you want to delete the group "rajah"?
This may leave files with invalid group ID in the file system.

I have checked rajah's folders and all are empty except for the "Examples" folder which everybody gets.

The nautilus debug file says:

"
===== BEGIN MILESTONES =====
0x8177880 2008/02/08 07:57:45.8953 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x8177880 2008/02/08 07:57:45.8955 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x8177880 2008/02/08 07:57:45.8956 (GLog): Can not get _NET_WORKAREA
0x8177880 2008/02/08 07:57:45.8956 (GLog): Can not determine workarea, guessing at layout
0x8177880 2008/02/08 08:05:17.9346 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9350 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9352 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9353 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9354 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9356 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9357 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9358 (USER): debug log dumped due to signal 11
0x8177880 2008/02/08 08:05:17.9360 (USER): debug log dumped due to signal 11..."
etc.

Could this be the reason why the firfox net window only holds for a moment before vanishing?

Regards

John

---

