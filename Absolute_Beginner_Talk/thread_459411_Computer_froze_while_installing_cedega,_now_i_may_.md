---
title: "Computer froze while installing cedega, now i may be screwed"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-30
While cedega was installing, I stupidly got curious and clicked the "terminal" text underneath the progress bar and it immediately froze, then firefox froze, then i couldn't even make the power button at the top right work.

So I had to do a hard shut down, when i rebooted everything seemed fine, I tried to run the package again and it seemed to open fine but then it told me that I cannot have any other package managers open at the same time. I didn't, but I decided to open and close synaptic just in case.

When I tried to open it, it gave me an error telling me I needed to manually run "sudo dpkg --configure -a", I did so, it gave no output and I went back and tried to open synaptic again, now it's saying 

```
E: The package cedega-small needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

all I can click is close, and that closes the program. When I try to open the cedega package again, it says

```
Could not open 'cedega_small_6.0_all.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
```

I deleted it and redownloaded it from the transgaming website to make sure it isn't corrupted, and I'm still getting the same error.

halp plz

---

### Post by zvacet on 2007-05-30
```
sudo apt-get --purge remove file_name
```

or if you want to do it manualy

```
whereis file_name
```

and after that go to the every folder and delete Cedega.When you are done reinstall it.

---

