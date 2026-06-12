---
title: "changing permissions for a whole directory"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Draddy on 2007-05-14
Hello, I was able to use a sudo chown -R david:david /opt/azureus to change permissions to the top folder... but how do I change permissions to that folders content?

thanks!

---

### Post by jclaybaugh on 2007-05-14
The command you ran above will change the ownership of the files and directories recursively. If you ran an ls -al command you will see that each file/directory including /opt/azureus is owned by user david and group david -

If you want to change permissions (read/write/execute) to the files in those directories, check out the chmod command (use the -R if you want the permissions to be set recursively).   

Hope that helps!

---

### Post by Draddy on 2007-05-14
I cannot figure out what to type.... sudo chmod -R /opt/azureus  does not work.. it is looking for a mode of sorts... the only option chmod --help gives is rfile, but it doesn't recognize that..

---

### Post by Tomosaur on 2007-05-14
> **Draddy said:**
> I cannot figure out what to type.... sudo chmod -R /opt/azureus  does not work.. it is looking for a mode of sorts... the only option chmod --help gives is rfile, but it doesn't recognize that..

That's because you're supposed to give a permissions setting too, for example:
```

sudo chmod -R 755 /opt/azureus

```
Would give:
Owner - Read, write, and execute permissions
Group - Read and execute permissions
Everyone else - Read and execute permissions

---

