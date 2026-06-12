---
title: "MySql Connector install problem :("
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Adie Stuart on 2007-05-12
could anyone tell me where i am going wrong with this installation. I downloaded mysql-connector-java-5.0.5.tar.gz and it saved it to my desktop, which i assume is the default for Firefox.

After the download was complete i then went to Terminal and entered the following

tar xfvz mysql-connector-java-5.0.5.tar.gz-C/opt/

but i got the following error message

adie@adie-laptop:~$ sudo tar xfvz mysql-connector-java-5.0.5.tar.gz-C/opt
Password:
tar: mysql-connector-java-5.0.5.tar.gz-C/opt: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
adie@adie-laptop:~$ 

After this failure, i then tried to extract the files straight to /opt folder, however, for some reason it wouldnt let me do that as i did not have the right permission to accesss this folder.

this is definately a lot more difficult than i first imagined Linux to be, but hell, it has to get a little easier doent it?  :(  :confused:

---

### Post by Cypher on 2007-05-12
First, do
```

tar -ztvf mysql-connector-java-5.0.5.tar.gz

```
This will list the contents of the file, including any directories that are contained within it. Then
```

cd /opt
sudo tar -zxvf ~/Desktop/mysql-connector-java-5.0.5.tar.gz

```
This will extract the contents..

---

### Post by Adie Stuart on 2007-05-12
Very many thanks to you Cypher, that worked a treat  =D> =D> =D>

---

