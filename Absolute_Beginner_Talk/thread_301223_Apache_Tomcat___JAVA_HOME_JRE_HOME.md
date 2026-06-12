---
title: "Apache Tomcat   JAVA_HOME JRE_HOME"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by ctrlcctrlv on 2006-11-16
Hello.


Im trying to get tomcat working on my Ubuntu Dapper install

its telling me this:

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

ok. so i head for the forums...wow...anyways here i am at the best forum in the universe. so far i have done the following:

1) I opened my .bash_profile, as instructed, and entered the folowing true information about the location of my jvm:

export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06

Is this the right thing to do?
I made this change and i ran:

2) source ~/.bash_profile

nothing happened i still get the same "neither nor" message.

How do i set the JRE_HOME? What file do i modify? 

What i really need is some clear directions, I hope someone out there has Tomcat 6.0 running.


ctrl

---

### Post by wieman01 on 2006-11-16
You can also definde the variables & set the paths in the script/batch file you are executing to run Tomcat. That's what I used to do in the past.

---

