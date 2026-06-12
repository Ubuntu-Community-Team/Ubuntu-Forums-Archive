---
title: "Shell Scripting Help!"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by brentos2004 on 2007-12-19
I Have a basic script that unzips a load of zip files. The zip files are password protected so the script contains a range of passwords that are used to unzip the folders. 

What I want to be able to do is to run a check on each folder once unzipped to confirm that two particular files are contained within the unzipped folders ie file1.mdb and file2.mdb. I need it to perform this check after it has unzipped each individual folder. I would like it to just carry on with the process of unzipping if the files are there and if there not there then write to a file which will then be emailed after the process is complete. 

Can these checks be done and is it possible to get the script to automatically email the log file after the script has completed? 

Any help would be appreciated. 

Here is the basic script at the moment.

#!/bin/bash
for Z_FILE in '/location/*.zip'; do
for PASSWD in [ password1, password2, password3 ]; do
unzip -P $PASSWD $Z_FILE;
if [ $? = 0 ]; then # successful unzip
break
fi
done
done

Thanks

---

### Post by slimdog360 on 2007-12-19
I dont know much about shell scripting, but I know python has some very nice email features, probably easier.

[http://docs.python.org/lib/lib.html]("http://docs.python.org/lib/lib.html") check chapter 7. If you're able to pick up shell you should be able pick up basic python really easy. Its you're choice though.

edit: I just thought about it, it is probably easier for you to just open the default email client and paste in your log file. Unless of course you wanted it to be done seamlessly.

---

### Post by brentos2004 on 2007-12-19
Hi Thanks for your reply I will take a look at this and see if its going to work. With the email I would like it to be done seamlessly but if thats the quickest option I will probably try that. 

Any other help/comments appreciated.

---

### Post by nick_h on 2007-12-19
You can test to see if a file exists with:
```
if [ -e filename ]; then
```

Have a look [here](http://www.linuxcommand.org/wss0090.php) for more details.

To email from the command line consider using a simple mail program such as mailx.

---

