---
title: "undefined symbol: SetUserId what does that mean?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by yaloveda on 2008-02-28
Hi everybody,

I've have been struggling with this problem for close to 2 weeks now and can't figure out where to find the answer, I searched the forums and googled the internet for anything, but no result.

I'm trying to install PLjava with postgresql database, but each time I try to install it, it give me that error:

/opt/pljava# java -cp postgresql.jar:pljava.jar:deploy.jar org.postgresql.pljava.deploy.Deployer -database adempiere -user ***** -password ***** -install


org.postgresql.util.PSQLException: ERROR: could not load library "/opt/pljava/pljava.so": /opt/pljava/pljava.so: undefined symbol: SetUserId
        at org.postgresql.core.v3.QueryExecutorImpl.receiveErrorResponse(QueryExecutorImpl.java:1548)
        at org.postgresql.core.v3.QueryExecutorImpl.processResults(QueryExecutorImpl.java:1316)
        at org.postgresql.core.v3.QueryExecutorImpl.execute(QueryExecutorImpl.java:191)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.execute(AbstractJdbc2Statement.java:452)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.executeWithFlags(AbstractJdbc2Statement.java:337)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.execute(AbstractJdbc2Statement.java:329)
        at org.postgresql.pljava.deploy.Deployer.initJavaHandlers(Deployer.java:474)
        at org.postgresql.pljava.deploy.Deployer.main(Deployer.java:269)
--------------------------------------------------------------------------------------------------------------------

I've installed postgresql 8.2 , JDK 6 , (java 1.6) , on a Ubuntu 7.04  (no upgrades or anything like that)

I'm doing this to install Adempiere ERP, but so far this PLJAVA problem made me pull my hair!   
 I used the following page as my guide to install Adempiere:

[http://www.posterita.org/mediawiki/index.php/PostgreSQL_Installation_on_Ubuntu_%28with_PL/Java%29_for_ADempiere](http://www.posterita.org/mediawiki/index.php/PostgreSQL_Installation_on_Ubuntu_%28with_PL/Java%29_for_ADempiere)

I installed Adempiere on Windows with relatively less problems, I'm new with Ubuntu and so far I installed it like  10 times  just to try to figure out how to make Adempiere work on it.

Anybody have a clue?
Thanks everybody :)

---

### Post by RealPSL on 2008-03-01
Your program is looking for a missing function SetUserId. Most likely it is searching for another .so file to find that function in. You probably want to make sure that the output of ldd /opt/pljava/pljava.so does not return any errors like "file not found". However most likely pljava is expecting to find that function SetUserID in another binary and finding it.

---

### Post by yaloveda on 2008-03-02
ldd /opt/pljava/pljava.so
        linux-gate.so.1 =>  (0xffffe000)
        libjvm.so => not found
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d9f000)
        /lib/ld-linux.so.2 (0x80000000)

That is what I got from the command ldd
So this means it can't find libjm.so , right?
I searched for that file and  founded it on my computer, so why this file can't be found then?

Thanks for your help :)

---

### Post by RealPSL on 2008-03-03
Yes it means that it can not find libjvm.so. Although in doing a little research I do not believe that is the only problem that exists. You can temporarily fix the error ldd is reporting by adding the directory path to libjvm.so to the LD_LIBRARY_PATH variable e.g. export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/path_to_libjvm.so where /path_to_libjvm.so is the directory libjvm.so is in. If that fixes your problem then read the man pages for ldconfig to fix it permanently.

Regarding the SetUserId problem specifically I believe that the link below will explain your problem as I do not believe the information above will solve the problem.

[http://www.nabble.com/Pl-Java-broken-since-Postgresql-8.3-rc1-td14746321.html](http://www.nabble.com/Pl-Java-broken-since-Postgresql-8.3-rc1-td14746321.html)

---

### Post by yaloveda on 2008-03-03
First of all I want to thank you RealPSL for taking time to help me, thanks man!

Well, I tried what u said and it gave me the same error, I'm new here so I will state what I did exactly:

I wrote the code line "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/server/libjvm.so"
 ( where that is my path) in the command line, then I used the same install command again, I got the same error.
I even tried different paths to other libjvm.so files I have in my computer (gcj 4.1 and another  folder called java-6-sun right beside java-6-sun-1.6.0.00 folder) and of course each time the same stupid error!

That is pretty frustrating!
Is there any way I can install any postgresql with Pljava on any Ubuntu at all (or any distro if that is the problem!) ? I tried 6.10 , 7.04 and pljava is not working with either so far, I need this to work because I'm suppose to implement  Adempiere in my new job and my boss is waiting to see if I will really do it or not!
I was thinking, maybe I need to compile a clean pljava source from there site to work with postgresql 8.2.6 ?? 
And how do u compile pljava source anyway? what do u use and how do u do it?

Once again thanks man for your time and your precious help :)

---

### Post by dantam on 2008-03-03
Hi

I just figured this out since my previously working Adempiere installation on an Ubuntu server suddenly stopped working giving the same error message you are referring to.

What you need to do is to upgrade PLJava to 1.4. It doesn't work with 1.3 or lower (the version you got from Posterita's home page).

Get 1.4 from [http://pgfoundry.org/frs/?group_id=1000038&release_id=1024](http://pgfoundry.org/frs/?group_id=1000038&release_id=1024)

The installation instructions are the same.

---

### Post by zazuge on 2008-05-11
Hello guys i found the same problem
"libjvm.so"
but found the solution her
[http://www.posterita.org/mediawiki/index.php/PostgreSQL_Installation_on_Ubuntu_%28with_PL/Java%29_for_ADempiere#Installing_and_Configuring_PostgreSQL_8.2_for_Pljava](http://www.posterita.org/mediawiki/index.php/PostgreSQL_Installation_on_Ubuntu_%28with_PL/Java%29_for_ADempiere#Installing_and_Configuring_PostgreSQL_8.2_for_Pljava)

well to some it up you got to add to /etc/ld.so.conf
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/server/
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/native_threads/
and then run ldconf to reload libraries
check the java-6-sun path it appears it have a different name on some computers and thats if you even have java 6.

---

