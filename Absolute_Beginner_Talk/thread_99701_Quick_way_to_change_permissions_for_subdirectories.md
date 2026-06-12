---
title: "Quick way to change permissions for subdirectories?"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by Doomed_Tupperware on 2005-12-06
Is there any quick way I could just make all directories in my Music folder read/write/executable (for some reason they're all un-writable) without having to change the permissions one by one on each folder? It's really annoying when I  have to transfer new music into my folders.

---

### Post by frodon on 2005-12-06
Use the command "chmod -R 777 directory_name", it will change the rights recursively starting from a directory.
More informations here : [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by doclivingston on 2005-12-06
frodon's command will work, but will give all the files execute permissions. A slightly more correct version would be "chown -R a+w directory_name".

---

### Post by doitashimashite on 2005-12-06
[QUOTE=doclivingston]frodon's command will work, but will give all the files execute permissions. A slightly more correct version would be "chown -R a+w directory_name".[/QUOTE]

I think frodon's command is exactly the right answer to the question, which was how to set read/write AND execute permissions to these files.

---

### Post by frodon on 2005-12-06
It depends of the need, i advice Doomed_Tupperware to read the link i gave in order to understand what he do.
In my personal case i would use the "chmod -R 755 directory_name" command but unfortunately unix rights are not supported by my FAT32 partition.

So let us know if you wish more details about this command Doomed_Tupperware

---

### Post by doclivingston on 2005-12-06
[QUOTE=doitashimashite]I think frodon's command is exactly the right answer to the question, which was how to set read/write AND execute permissions to these files.[/QUOTE]

You're right, I mis-read the question. However I doubt that Doomed_Tupperware really wants to set the execute permission on his music files.

---

