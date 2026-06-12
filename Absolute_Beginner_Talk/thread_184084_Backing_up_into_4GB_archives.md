---
title: "Backing up into 4GB archives"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Or'Enn on 2006-05-29
Hi all.
I am in the process of backing up my entire /home directory, which is about 20 GB uncompressed to repartition the harddrive for Ubuntu dapper (Fedora Core sneaked in LVM). The archives will go to DVDs, so I was wondering: **How can I split a very big gzipped tar file into 4 GB chunks?** I have read through the man page for the tar command and can't seem to find an option to split the archive into "many" files based on size.
The split command has been mentioned, but I'm a bit cautious to use a command I've barely heard of to split a file that large.. is it safe?

tar -cjvpf backup-06-05-29.tar.bz2 ./
split -db 4000m backup-06-05-29.tar.bz2 backup-06-05-29-

And then assemble them using
cat backup-06-05-29-* | tar xjvp

---

### Post by shof2k on 2006-05-29
Erm I don't know the answer to your question, but you can back up your drive using dar.  Dar allows you to specify 'slices' for the backup file, be it CD or DVD.

It's availabe in the repros via ```
 sudo apt-get install dar 
```

---

### Post by Or'Enn on 2006-05-30
Thanks for the reply. I went with the manual route and it worked great, but it was a bit time consuming. Now to wait for dapper drake to finalize...

---

