---
title: "java is driving me nuts"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-04-16
so i reinstalled dapper because of a few problems which i made myself

and i had the newest java jre 1.5.0 iinstalled from the bin i got from the java website and when i did java -version it came back with 1.5.0

now the java.bin file from the java website wont take over and install right.. i still get 1.4.2 when i do java -version.. its driving me nuts

how come it worked fine before in dapper, and now it wont work? im doing the install the same way i did before!

i have java-common and java-package.. before i installed the bin, then had to remove those 2 and it worked fine.. now firefox wont do anything java!

its killing me

---

### Post by unbuntu on 2006-04-16
[QUOTE=joshrobinson]so i reinstalled dapper because of a few problems which i made myself

and i had the newest java jre 1.5.0 iinstalled from the bin i got from the java website and when i did java -version it came back with 1.5.0

now the java.bin file from the java website wont take over and install right.. i still get 1.4.2 when i do java -version.. its driving me nuts

how come it worked fine before in dapper, and now it wont work? im doing the install the same way i did before!

i have java-common and java-package.. before i installed the bin, then had to remove those 2 and it worked fine.. now firefox wont do anything java!

its killing me[/QUOTE]

It seems like you're having two separate installation of jre.

do a
```
which java
```
to see the path of the executable you're calling, and check if it's the path you installed your jre1.5

---

### Post by joshrobinson on 2006-04-16
[QUOTE=unbuntu]It seems like you're having two separate installation of jre.

do a
```
which java
```
to see the path of the executable you're calling, and check if it's the path you installed your jre1.5[/QUOTE]

it came back as usr/bin/java
i installed it to /java1.5.0 or something alogn those lines
can i change the path? or should i install my jre 1.5.0 to usr/bin/java?

---

### Post by unbuntu on 2006-04-16
[QUOTE=joshrobinson]it came back as usr/bin/java
i installed it to /java1.5.0 or something alogn those lines
can i change the path? or should i install my jre 1.5.0 to usr/bin/java?[/QUOTE]

I haven't tried this but you can rename the one in /usr/bin to something else, and create a symbolic link to the one in your jre1.5 directory.  Let me know whether it works.

Just in case you need the command for creating symbolic links:
```

ln -s /your/jre1.5/directory/bin/java /usr/bin/java

```

Once again, I'm not sure this will solve the problem.

---

### Post by joshrobinson on 2006-04-16
ok the sym link worked.. and now java -version comes back with the right version number

but firefox still doesnt handle java files right
such as the test java install website on java.com

any ideas to fix firefox? reinstall?

---

### Post by unbuntu on 2006-04-16
[QUOTE=joshrobinson]ok the sym link worked.. and now java -version comes back with the right version number

but firefox still doesnt handle java files right
such as the test java install website on java.com

any ideas to fix firefox? reinstall?[/QUOTE]

Well...another unexperimented approach:  use synaptic to uninstall the old copy of jre1.4, and install jre1.5 again.

---

### Post by joshrobinson on 2006-04-16
[QUOTE=unbuntu]Well...another unexperimented approach:  use synaptic to uninstall the old copy of jre1.4, and install jre1.5 again.[/QUOTE]

no go.. i removed them.. still get the right java -version.. but everytime i go to a java website on firefox i get that yellow bar that comes down and says im missing a plugin..

i even made the sym link into the firefox plugins folder to the plugin in my JRE directory

edit: it works in konquror but not firefox.. so at least im half way there

---

### Post by unbuntu on 2006-04-16
[QUOTE=joshrobinson]no go.. i removed them.. still get the right java -version.. but everytime i go to a java website on firefox i get that yellow bar that comes down and says im missing a plugin..

i even made the sym link into the firefox plugins folder to the plugin in my JRE directory[/QUOTE]

I've no clue then...except the following FAQ from Mozilla may of help:
[http://www.mozilla.org/support/firefox/faq#q2.2](http://www.mozilla.org/support/firefox/faq#q2.2)

Although it's speaking of jre1.4.2, it might be that your libraries in the firefox directory is mixed up.

---

### Post by joshrobinson on 2006-04-16
[QUOTE=unbuntu]I've no clue then...except the following FAQ from Mozilla may of help:
[http://www.mozilla.org/support/firefox/faq#q2.2](http://www.mozilla.org/support/firefox/faq#q2.2)

Although it's speaking of jre1.4.2, it might be that your libraries in the firefox directory is mixed up.[/QUOTE]

yeah i completely deleted the firefox dir in usr/lib/firefox and extracted everything from the newest firefox .tar file to that DIR and still no go

konq. works tho

---

### Post by joshrobinson on 2006-04-16
yay!!! i finally got it.. i was at that link you posted and did the sym link a few times.. then i realized some of the directories wernt right.. i was thinking that if the source file didnt exist then it wouldnt make the sym link and give an error

but i finally got it right and it works good now

thanks so much for your help!!

---

### Post by unbuntu on 2006-04-16
[QUOTE=joshrobinson]yay!!! i finally got it.. i was at that link you posted and did the sym link a few times.. then i realized some of the directories wernt right.. i was thinking that if the source file didnt exist then it wouldnt make the sym link and give an error

but i finally got it right and it works good now

thanks so much for your help!![/QUOTE]

Yes, if a symbolic link is broken, it will be coloured red when you do a "ls -l".

Glad you figured it out.

---

