---
title: "Rsync - Exclude Lists - I failed?"
date: 2012-03-28
forum: Any Other OS
---

### Post by Roasted on 2012-03-28
I'm trying to run rsync from my Macbook using an exclude list. However, things aren't exactly working for me and I'm not sure why.

In my home folder, I have a folder called "loginscript". Inside is login.sh and exclude.txt. I have login.sh with +x permissions as well as set to open with terminal and it's also set to run at login. Both of their contents are below:

```
rsync -az -e "ssh -p 12345" --delete --exclude-from '/Users/Jason/loginscript/exclude.txt' /Users/Jason/ jason@192.168.1.10:/media/NAS/jason/MacbookPro
```


```
Library
Music
VirtualBox VMs
.*
```

Problem is, I'm still getting all of the above folders... Any ideas?

---

### Post by CharlesA on 2012-03-28
Does it do the same thing if you do the excludes individually? I haven't tried using a list in my rsync script.

---

### Post by SeijiSensei on 2012-03-28
> **CharlesA said:**
> Does it do the same thing if you do the excludes individually? I haven't tried using a list in my rsync script.

I've used --exclude-from many times and never had this problem. I do using trailing slashes in the list like this:

```

proc/
sys/
lost+found/

```

though I don't see why that would matter.  

Try running rsync with -avvvn as the options.  This will provide the most verbose output (three "v's") and will not actually transfer any files (the -n "dry-run" option as the man page describes it).

---

### Post by papibe on 2012-03-28
AFAIK, these rules should work. First guess would be to double check the exclude path and filename.

BTW, what is rsync's version on the Mac?
```
rsync --version
```
Regards.

---

### Post by Paddy Landau on 2012-03-30
I think it would be a good idea for you to carefully read the section "[INCLUDE/EXCLUDE PATTERN RULES]("http://manpages.ubuntu.com/manpages/precise/man1/rsync.1.html#contenttoc16")" in the [rsync manual]("http://manpages.ubuntu.com/manpages/precise/man1/rsync.1.html").

Your current set-up may accidentally exclude files and folders that you'd rather keep. Try using leading and trailing slashes, as:
```
/Library/
/Music/
/VirtualBox VMs/
/.*
```You may need to experiment with the leading slash, depending on the root folder where you start your command. An alternative would be:
```
**/Library/
**/Music/
**/VirtualBox VMs/
**/.*
```This would (potentially) exclude more that the previous option.

---

