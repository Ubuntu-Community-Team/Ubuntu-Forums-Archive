---
title: "Installing netbeans Javadocs"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by mike_g on 2007-12-15
Hello people! I recently started using Ubuntu and installed netbeans5.5. I seem to be missing some javadocs tho that get installed with the windows version.

Basically the netbeans docs are there but when the code completion comes up it only tells me the function prototype. Where theres usually a description it says that the javadocs are not found and they should be added in the platform or library manager.

Anyway I went there and it want to install from zips I havent got. So I figured I'd use apt-cache search to see if I could install them that way. That gave me a list of lots of stuff that made me confused.

Basically I just want the docs explaining the methods for basic java, swing, and awt. Anyone know what files it is i want to be getting, and can I do it all with apt-get?

Cheers.

---

### Post by jken146 on 2007-12-16
A quick search on packages.ubuntu.com revealed that there's a package called netbeans5.5-doc -- this sounds like what you want.  (You can also search in Synaptic)

---

### Post by mike_g on 2007-12-16
Nah I tried that and it dident seem to work. I think thats just documentation on the IDE that comes with the netbeans5.5 package anyway.
 
edit: I'll try search fro synaptic tho. Cheers.

---

### Post by edigs on 2007-12-19
You probably already found answer by now but anyway. I managed to get it working by installing sun-java6-doc (or sun-java5-doc for java5) using apt-get (you have to download additional files from Sun - follow instructions) and then restarting netbeans.

---

### Post by mike_g on 2007-12-23
> You probably already found answer by now but anyway. I managed to get it working by installing sun-java6-doc (or sun-java5-doc for java5) using apt-get (you have to download additional files from Sun - follow instructions) and then restarting netbeans. 

Actually I had kind of forgotten about sorting out the javadocs until today. Anyway I did what you said and it works a treat. Thanks :)

---

### Post by Ryzol on 2008-02-21
I know this is an old thread but this information was helpful to me and should save people from redudant threads.

> **edigs said:**
> You probably already found answer by now but anyway. I managed to get it working by installing sun-java6-doc (or sun-java5-doc for java5) using apt-get (you have to download additional files from Sun - follow instructions) and then restarting netbeans.
Just want to say thanks, this helped a lot. I had trouble finding the javadocs after they were installed, in case anyone else is struggling with this mine were in /usr/lib/jvm/java-6-sun/docs/api. The path without symbolic links is /usr/share/doc/sun-java6-jdk/html/api.

---

### Post by sephirot_5 on 2008-07-04
Hi, i also have the same problem here, but installing the sun-java-doc (and downloading and placing asked files) doesn't work, can you help me please? :)

---

### Post by jamesstansell on 2008-07-04
Will the openjdk-6-doc package work for you?  It should have essentially the same information.

---

### Post by sephirot_5 on 2008-07-05
> **jamesstansell said:**
> Will the openjdk-6-doc package work for you?  It should have essentially the same information.

=Ok, let me try, and i'll post the result :)

---

### Post by sephirot_5 on 2008-07-05
> **sephirot_5 said:**
> =Ok, let me try, and i'll post the result :)
I've just installed it and no, still the same problem :(

Javadoc not found. Either Javadoc documentation for this item does not exist or you have not added specified Javadoc in the Java Platform Manager or the Library Manager


What could it be?

---

### Post by sephirot_5 on 2008-07-06
> **sephirot_5 said:**
> I've just installed it and no, still the same problem :(

Javadoc not found. Either Javadoc documentation for this item does not exist or you have not added specified Javadoc in the Java Platform Manager or the Library Manager


What could it be?


GOT IT WORKING!!!!

All i have to do was removing several packages aptitude installed when i installed netbeans, and i don't know how, it started working :)

---

