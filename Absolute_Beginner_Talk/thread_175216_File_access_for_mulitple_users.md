---
title: "File access for mulitple users"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by mtbiker on 2006-05-13
Hello,
  I've got 3 people that have access to my computer via 3 seperate usernames.  I've got a folder with files in it I would like to share with them and would like them to have all access to those file.  What's the right way to go about doing this in Ubuntu?

With the very little Linux knowledge I do have, here's what I've done.

On the root of the my drive I did a "sudo mkdir files" to make the directory called file.  I then did a "sudo chmod 777 files" to give them access.  777 is complete access to read/write/create/delete isn't it? The other users can access the folder, can create files on it, but I can't view the files.  I get a "access denied" message.

Sorry for the stupid question.  I'm really new to Linux.  

Thanks,
Mark

---

### Post by eentonig on 2006-05-13
A more logical way, would be to make a group for these users. And then give this groups the permissions required. That way, unauthorized users still can't see /use these files. And if later on you want someone else to be able to access these files as well, you just have to include that user in the group.

---

### Post by mtbiker on 2006-05-13
Thanks, that's a good idea.  I did that, but I still don't know how to give that group or users full rights to that folder.

Thanks,
Mark

---

