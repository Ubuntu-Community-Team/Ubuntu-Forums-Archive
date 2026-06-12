---
title: "How to turn a java .bin ito .deb"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Ultros88 on 2008-02-11
Hello,
I'm trying to turn jdk-6u4-linux-i586.bin into a .deb so I can install it. I have fakeroot and java-package installed.

When I run: >fakeroot make-jpkg jdk-6u4-linux-i586.bin

I get: 
  Creating temporary directory: /tmp/make-jpkg.rebeVQ7475
  Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

  Detected Debian build architecture: i386
  Detected Debian GNU type: i486-linux-gnu

  No matching plugin was found.
  Removing temporary directory: done

What's the deal? Why doesn't this work? What are these plugins?
Thanks all.

---

### Post by taurus on 2008-02-11
Shouldn't it be easier to move jdk-6u4-linux-i586.bin to where you want to install/unpack and install/unpack it from a terminal?

```
sudo mv jdk-6u4-linux-i586.bin **<destination>**
sudo chmod 755 jdk-6u4-linux-i586.bin
sudo ./jdk-6u4-linux-i586.bin
```

---

### Post by Ultros88 on 2008-02-11
Yeah, that works.

However, I should have prefaced my original message with my initial problem. I am learning java and try to test an applet I developed. The .java file compiles fine but when I open the html file containing the code:

<applet code="StaticRects.class" width=300 height=160></applet>

All I get is a black applet window.

I read online about a problem in fire fox that requires jdk-6u4 in order to be rectified so I dowloaded that .bin file.

Now I'm not really sure what to do with the extracted files to fix my initial problem of "why on Earth won't the applet run?".

Again, help is much appreciated.

---

