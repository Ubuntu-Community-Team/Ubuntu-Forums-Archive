---
title: "Checking user account access rights?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-08-19
How do I check the access rights that a user account has?

I have created some new users and I "think" they are being created with root access by default.

How do I go about checking?

Thanks.

---

### Post by mrsticks on 2007-08-19
You can go to System->Administration->Users & Groups.

You can check the properties on a user, there is a User Privileges tab in there.  Pretty descriptive checkboxes for things the user can / cannot do.

In the User Settings box, there is a Manage Groups button.  If you click that, than click the Properties button on the root group, you can see who is a member of that group.

I am pretty sure this tool is a GUI for editing /etc/passwd and /etc/group

-peter

---

### Post by aysiu on 2007-08-19
No user in Ubuntu has root access by default. Certain users (the ones in the *admin* group) can temporarily attain root access for specific tasks by invoking *sudo* and authenticating with a password.

---

### Post by AnotherMuggle on 2007-08-20
[QUOTE=aysiu]No user in Ubuntu has root access by default. Certain users (the ones in the *admin* group) can temporarily attain root access for specific tasks by invoking *sudo* and authenticating with a password.[/QUOTE]

[QUOTE=mrsticks]You can go to System->Administration->Users & Groups.

You can check the properties on a user, there is a User Privileges tab in there. Pretty descriptive checkboxes for things the user can / cannot do.

In the User Settings box, there is a Manage Groups button. If you click that, than click the Properties button on the root group, you can see who is a member of that group.

I am pretty sure this tool is a GUI for editing /etc/passwd and /etc/group

-peter [/QUOTE]

Thanks for the responses.

What does confuse me, is that if I look at the "root" user under Users & Groups, none of the check boxes are ticked.  It looks like the account has less access than the other accounts. :S

Oh and it looks to me like this blanking of the screen with a "Please enter an admin. password" idea has so been pinched by M$ for the UAC idea?!

---

