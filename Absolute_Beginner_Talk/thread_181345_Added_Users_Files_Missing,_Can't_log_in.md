---
title: "Added Users Files Missing, Can't log in"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-24
I created another user for a member of my family.

After not logging in for a while, I can't log the account it.  Says files are missing.

I have to try to log in again to give you the error messages.

**How do I delete the account and re-create it? ** I ask because I don't want to go searching through my directories looking for the hidden files it is missing.  Yeah, Why are their missing hidden files?  I haven't a clue.  I don't think I moved them.  I know I didn't move them on purpose.  I don't even remember accessing the account for anything.

Thanks.

---

### Post by Mustard on 2006-05-24
Can you remember how you added the new user account?

To delete a user, open a terminal and type in this command (don't delete the wrong user)
```
sudo deluser user_name --remove-home
#subsitute the correct username for 'user_name'
#drop the --remove-home option if you want to retain the
#home directory for that user
```

To add a user

```
sudo adduser user_name
#this will set up a simple user account
#you may need to add the user to certian groups
#to make the user account have access to particular
#devices
```

You can see the groups that users belong to with this command.

```
cat /etc/group
```

or

```
groups user_name
#this will return the groups that a user is part of
```

You can also go to the System>>Administration>>Users and Groups menu option and add or delete users from there.  The delete option in this gui doesnt seem to support deleting the home folder of the user though.

---

