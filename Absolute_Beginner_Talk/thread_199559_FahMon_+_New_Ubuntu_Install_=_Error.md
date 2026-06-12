---
title: "FahMon + New Ubuntu Install = Error"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by TelePunk5 on 2006-06-18
Hello. I'm new to these forums, so if this was an inappropriate place to post this question, feel free to move it. I recently switched over to Dapper from Breezy. I must say Dapper is wonderful and I can really see the difference. I'm already excited for Edgy.

I have hit one little snag with Dapper, and I haven't been able to fix it myself so I thought I would post here. I participate in Folding@Home and I used FahMon to monitor my progress on 5.10. I decided to reinstall FahMon after I upgraded to 6.06. I did the following;

```
sudo apt-get install libgtk2.0-0
sudo apt-get install libwxgtk2.6-0
sudo apt-get install scons
```

These are the dependencies listed in the FahMon documentation. The next step in the install is changing into the source directory and doing scons. From there it should just be a matter of executing the program. This is what happened when I tried.

```
telepunk5@compy:~/FahMon/src$ ./fahmon
./fahmon: error while loading shared libraries: libwx_gtk2_xrc-2.6.so.0: cannot open shared object file: No such file or directory
```

I know that there is an Ubuntu folding team, so perhaps someone can help me with this issue. Thanks in advance.

---

