---
title: "how do you make a script and execute it"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by oehq on 2008-04-06
I am trying to make a script that I can run dailly to backup my data files to an external usb drive. 
I have tried this little test which just takes me to the folder I want to tar.

I can not even get this to run

#!/bin/sh  
 cd /
 cd /media/disk/LS01-raid_data
 ls

I created the file godata.sh with gedit  using the script above and saved it with a sh extension.

I then did 
chmod +x godata.sh 

To make it executable

However when i run the script i get the following

ls01@ls01-Dserver:~/bat$ godata.sh
bash: godata.sh: command not found

:confused:

can someone tell me what I am doing wrong???

Thanks for the help

Heff

---

### Post by InfinityCircuit on 2008-04-06
Since your working directory is not in your $PATH, you have to invoke the script with a trailing backslash:

```
./godata.sh
```

Alternatively if you didn't want to make the script executable you could invoke it with:
```
sh godata.sh
```

---

