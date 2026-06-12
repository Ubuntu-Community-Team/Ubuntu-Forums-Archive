---
title: "Users and Groups"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by James Maxwell on 2006-12-14
Hi Guys

I have an issue with users and groups.

I am trying to set up permissions and have created 2 groups which I can add users to. Although I have added the user I am logged in as when I use the ‘groups’ command it does not tell me the groups I have just added a user to are there. 

Any ideas??

Thanks 

James

---

### Post by James Maxwell on 2006-12-14
This is using the tereminal by the way, i am remotely logged on.

---

### Post by taurus on 2006-12-14
How did you add those users to the groups?  Did you add them to /etc/group?  What does /etc/group look like then?

```
cat /etc/group
```

---

### Post by James Maxwell on 2006-12-14
Private:x:1006:jameshannah,administrator
private:x:1007:rob,james
data:x:1008:james,rob,david,jameshannah,administrator



I just realised i have not added them to the private group becasue there are 2 one called Private one called private. and the groups are in here but not when i type groups as a command.

also as a second how do i do a chmod for a whole tree not just the specified folder i want everything in that folders permissions to change as well also group ownership so the Private folder belongs to the private group etc.

i managed to get samba to write with group permissions and the correct 770 permissions which in one plus.

Thank you for youe help so far taurus.

James

---

### Post by taurus on 2006-12-14
```
sudo chmod -R 755 **directory**
sudo chgrp -R **group-name** **directory**
```

---

