---
title: "i did something weird during my install..."
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by polkadotchickens on 2006-01-11
ok, so i did an expert install of breezy at my linux-pro-boyfriend's request so i could try to install something specific (didn't end up working out...long story...had a hell of a time getting it to work...but it does now.  anyway).  when i did that, i set up a root password because i thought i had to.  now i know better, but instead of reinstalling i'd like ot learn to fix or to cope with what i did.  i know how to use su instead of doing the sudo thing like would be normal, but i'm having problems accessing things like network stuff and synaptic and now the update function through graphical menus.  it prompts me for my password, and neither my user password nor my root password will give me access.  i can do some of these things in terminal, but not very much because i really don't know what i'm doing.  what password does it want?  how can i fix these things?  help?

---

### Post by bluefrog on 2006-01-11
asking for root password during a server install is the "normal way". for new created users you will have to add them to sudoers.

visudo     to edit the sudoers file


during a normal install you don't have to do that as the install created user group is added automatically to the sudoers.

james

---

### Post by polkadotchickens on 2006-01-11
woo!  ok, thanks, a whole lot! i initially said "HUH?!?" to your reply, but editing visudo to fix my issue is well-covered on the forum.

---

