---
title: "How to set permissions on Mac to allow read/write on Ubuntu?"
date: 2011-09-19
forum: Apple Hardware Users
---

### Post by CosmicVoyager on 2011-09-19
Greetings,

How do I set the permissions on a Mac drive so that if I plug into a computer running Ubuntu I can read & write? "Everyone" Read & Write does not work.

Thanks

---

### Post by CosmicVoyager on 2011-09-19
Greetings,

I am trying to copy a hard drive from my Mac computer, but it says it can't copy because I do not have permission to read the files?

Any way around this?

Thanks

---

### Post by mörgæs on 2011-09-19
Please don't create multiple threads on the same question. Threads merged.

---

### Post by coffeecat on 2011-09-20
The hard drive, or at least the partition you are trying to read, will be formatted with the journalled version of the hfs+ filesystem, which you can read but not write to in Ubuntu. (Actually, you can, but that requires a force mount workaround which I personally wouldn't use.) If you are trying to change permissions in Ubuntu you will get either a "read-only" error if you invoke sudo rights, or a permissions error if you try to do it as an ordinary user. The reason you get a permissions error as an ordinary user is that your UID in Ubuntu is (probably) 1000 and in your Mac files, 501.

Easy workaround. Use a root nautilus invoked with "gksudo nautilus". You will be able to browse and copy at will, However, this will probably have the effect of making any files you copy to a Linux filesystem to be owned by root. If you need any help changing the ownership of those, post back.

---

### Post by CosmicVoyager on 2011-09-20
"Use a root nautilus invoked with "gksudo nautilus"."

I don;t know what this means :-(

I have been trying all day everyday for several days to copy the drive. It's a nightmare.

Isn't there a way to be the same user on all computers so I can just plug the drive in any computer and have full access? Should it work if I use the same name?

---

### Post by coffeecat on 2011-09-20
> **CosmicVoyager said:**
> 
I don;t know what this means :-(


Sorry, I didn't make that clear. Open a terminal, and:

```
gksudo nautilus
```

That will open a root nautilus, but in root's own folder. You'll have to go up a level to the system filesystem and then find the drive mountpoint, open that and navigate your way to your Mac files. If you need help with that we'll need some more information.

With regard to your other question, you can set more permissive permissions if you put the drive back into the Mac. Can you do that? The best thing is to describe exactly what you are trying to do. Is this the internal drive from a Mac which you've put in an USB enclosure, or is this an external drive that you've formatted in the Mac Disk Utility?

---

