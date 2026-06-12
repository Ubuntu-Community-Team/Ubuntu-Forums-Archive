---
title: "Cannot install Java 6.0"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by atze76 on 2006-12-11
Hi,
I have just downloaded the latest Java SDK 6.0. I wanted to generate a .deb file using fakeroot make-jpkg as described somewhere:

[FONT="Fixedsys"]fakeroot make-jpkg jdk-6-linux-i586.bin[/FONT]

Unfortunately no .deb file was generated and I only got the following output:

[FONT="Fixedsys"]Creating temporary directory: /tmp/make-jpkg.XXXXgQSNji
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done[/FONT]

I also tried the following command:

[FONT="Fixedsys"]DEB_BUILD_GNU_TYPE=i386 fakeroot make-jpkg jdk-6-linux-i586.bin[/FONT]

The output was the same as above (that there is no matching plugin). Does anybody have an idea? The "fakeroot make-jpkg" procedure used to work with older java SDKs like 1.5.0.6 and 1.5.0.7

cheers

---

### Post by John.Michael.Kane on 2006-12-11
Maybe of use.
[http://ubuntuforums.org/showthread.php?t=213850&page=2](http://ubuntuforums.org/showthread.php?t=213850&page=2)

---

### Post by atze76 on 2006-12-11
That's quite a lot of work :-? so I haven't tried it yet. Isn't there an easier way?

---

