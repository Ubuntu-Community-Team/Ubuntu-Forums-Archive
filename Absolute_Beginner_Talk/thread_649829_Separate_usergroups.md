---
title: "Separate usergroups?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by graabein on 2007-12-25
Hello I have installed Xubuntu 7.10 on my family's computer and am wondering how to set up usergroups. I now have the following **/home**:
[LIST]
[*]graabein
[*]mom
[*]dad
[*]sister1
[*]sister2
[*]shared
[*]lost+found
[/LIST]

What owner:group should I have for the directories? Right now it's a bit all over the place. I have usergroups for each user (mom group, dad group etc) but that seems a bit unnecessary? 

:confused:

---

### Post by phosphoricx on 2007-12-25
Yeah that is overkill. Basically you can assign permissions two ways in Linux:

1) By user
2) By group

So if you want a particular family member to only have access to his or her own files, then you can leave the permissions as is. However, if you want to be able to access files for everyone in your family. Then you could change everyone to the "Family" group.

Personally I wouldn't do it unless the need comes up, but it's not difficult. Here's a link for more details:

[ Users in Ubuntu]("http://www.freesoftwaremagazine.com/articles/users_in_ubuntu?page=0%2C1")

Good luck!

---

