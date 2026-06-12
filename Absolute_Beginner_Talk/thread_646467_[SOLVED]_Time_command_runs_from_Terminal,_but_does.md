---
title: "[SOLVED] Time command runs from Terminal, but does not run in sh file"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-12-21
Hi,
I executed the following command from Terminal:
\time -p -o output_file.txt sleep 2

The output was written to ouput_file.txt. So far so good.
But saving the command in sh file and executing it from Terminal the command doesn't run.

Any idea how to execute above command from file?

Thanks,
Abcuser

---

### Post by barbedsaber on 2007-12-21
umm, this down't seem to fit in absolute beginer talk.

---

### Post by hyper_ch on 2007-12-21
post your whole .sh file please.

---

### Post by abcuser on 2007-12-21
Hi,
the whole script is idea to measure SQL statements executed against IBM DB2 Express-C database (free ware).

So the script is like this:
> db2 connect to sample 
\time -p -o out.txt db2 "select * from sysibm.sysdummy1"
cat out.txt  | grep real | cut -c6-16 > out.txt 
But "\time..." command returns error "Database connection does not exist".

I have found out that Linux time command is probably executing in new process (new Terminal), so I have found out that both commands connect and select must be executed in one command with or atribute.

So this works fine:
> \time -p -o out.txt db2 connect to sample || db2 "select * from sysibm.sysdummy1"
cat out.txt  | grep real | cut -c6-16 > out.txt 

Thanks. Problem solved.
Abcuser

---

