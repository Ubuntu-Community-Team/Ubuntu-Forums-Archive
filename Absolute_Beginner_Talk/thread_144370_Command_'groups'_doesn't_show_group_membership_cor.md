---
title: "Command 'groups' doesn't show group membership correctly"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-14
# display the groups user 'dovecot' is in
$groups dovecot 
dovecot : dovecot mail 
# as shown, user 'dovecot' is in group 'dovecot and group 'mail'

# display the group user 'mail' is in
$groups mail 
mail : mail
# as shown, user 'mail' is in group 'mail'

# check who are the members of group 'mail' and I should see user 'dovecot' and user 'mail'
$cat /etc/group |grep mail 
mail:x:8:dovecot 
# however, I only see user 'dovecot' here

Is there a reason why user 'mail' is not shown as a member of group 'mail' in the last command?

Thanks!

---

### Post by jobezone on 2006-03-14
I don't know why that is. I don't usually mess much with groups, but can't you just edit */etc/group* and add the user mail in the group mail, to look like:

mail:8:doveco,mail

?

---

