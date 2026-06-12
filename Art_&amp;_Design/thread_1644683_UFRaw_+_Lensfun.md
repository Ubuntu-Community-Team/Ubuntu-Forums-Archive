---
title: "UFRaw + Lensfun?"
date: 2010-12-13
forum: Art &amp; Design
---

### Post by wadam on 2010-12-13
Hello all --

Is there a PPA out there where I can get a version of UFRaw 0.17 with lensfun functionality enabled?  I know that a version of 0.17 can be had here:

```
ppa:ferramroberto/maverick
```

But those packages don't seem to provide access to lensfun.

I ask only because, after trying several RAW converters including Bibble 5, UFRaw seems to be the only one that provides really good results with my Oly EP-2.  But unfortunately, lens correction is kind of a must for that camera.

---

### Post by Rodney9 on 2010-12-13
> The status of the lensfun code in UFRaw

One of the most interesting feature that was added to UFRaw recently is the use of the lensfun library. This allows the user to correct lens distortions, making straight lines straight. Moreover, lensfun also includes a large database of lenses with the parameters required to fix their distortions. This makes the process of applying the lensfun corrections almost automatic.

Still, this code in UFRaw is in experimental condition and should not be used unless the user understands the cavities involved in using the code. If you are building UFRaw from source, read this page and decide for yourself if you want to enable this feature (./configure --with-lensfun). For distributed packages, it is not recommended to enable lensfun, since most users would not be aware of the problems involved in using this feature. Personally, as the distributed of the win32 version of UFRaw I am not planning to enable this feature for MS-Windows users.

The cavities in the current code (as of UFRaw 0.14 and 0.15) are:

    * The lensfun parameters are not written to UFRaw ID files. This means that if you create an ID file and use it to convert a batch of photos, no lensfun corrections will be applied. Also, reprocessing an image with its original ID file should generate the same output as the last time the image was converted. This is not the case if you apply lensfun corrections as those would disappear. Lastly, the option "Send to Gimp" also relies on the ID file. Therefore images sent to Gimp will loose the lensfun corrections.
    * At the moment the lensfun correction is applied at the wrong point during the image conversion workflow. It should be applied on the linear data before the ICC profile, but at the moment it is applied afterwards. In many cases the difference in the output is academic, still I believe in doing things the right way (tm). In some cases this leads to strange behaviors. For example, applying chromatic aberration correction to a grayscale images causes color artifacts. Another problem is that the parameters used for vignetting corrections are difference if you apply the correction before or after the ICC profile. This means that users that would add those parameters to the lensfun database based on the current implementation in UFRaw would get the wrong results after UFRaw will be fixed.
    * UFRaw requires the latest code from lensfun SVN. It is not healthy to distribute code that cannot be mapped to a specific released version of a library. (lensfun 0.2.3 was released)
    * The lensfun feature almost doubled the number of controls in UFRaw's GUI. Therefore it will take a while to fix all the bugs in the GUI to get a smooth and predictable behaviour.

I hope I gave you enough information to decide if you are ready to use lensfun in UFRaw. from - [http://ufraw.sourceforge.net/lensfun.html](http://ufraw.sourceforge.net/lensfun.html)

UFraw 1.6 is available in synaptic as well as Lensfun

or 

you can follow the insructions here - [http://ufraw.sourceforge.net/Install.html](http://ufraw.sourceforge.net/Install.html)

---

### Post by wadam on 2010-12-13
Thanks for the quick response.  I'd be perfectly happy with 0.16 + lensfun enabled.  But the version of UFRaw in the default Ubuntu distribution does not, in fact, have lensfun installed.

I could build UFRaw from source, as per the instructions.  But I'm not sure how to roll .debs at home, and I don't want to go installing programs independently of the package manager.

What I'm looking for, optimally, is a package repository.  And barring that, as a last resort, simple instructions on rolling my own package would not be amiss.

---

### Post by earlycj5 on 2010-12-13
> **wadam said:**
> Thanks for the quick response.  I'd be perfectly happy with 0.16 + lensfun enabled.  But the version of UFRaw in the default Ubuntu distribution does not, in fact, have lensfun installed.

I could build UFRaw from source, as per the instructions.  But I'm not sure how to roll .debs at home, and I don't want to go installing programs independently of the package manager.

What I'm looking for, optimally, is a package repository.  And barring that, as a last resort, simple instructions on rolling my own package would not be amiss.

Try Pascal's PPA: [https://launchpad.net/~pmjdebruijn/+ppa-packages](https://launchpad.net/~pmjdebruijn/+ppa-packages)

---

### Post by wadam on 2010-12-13
Alas.  Available from Pascal's PPA for Karmic and Lucid, but not for Maverick.

---

### Post by earlycj5 on 2010-12-13
> **wadam said:**
> Alas.  Available from Pascal's PPA for Karmic and Lucid, but not for Maverick.

I've got 0.17 installed on my system(s) from Pascal's PPA.

---

### Post by wadam on 2010-12-13
I don't seem to be able to find it from his PPA.  What does your repository line look like?  Thanks.

---

### Post by earlycj5 on 2010-12-14
```

deb http://ppa.launchpad.net/pmjdebruijn/darktable-unstable/ubuntu maverick main
deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-unstable/ubuntu maverick main

```

Perhaps because I'm using the unstable repository for Darktable?

---

### Post by wadam on 2010-12-14
I'll try that.  I've tried his build of Darktable, which I like quite a bit.  But I don't really want or need the organizational features that it offers.

---

### Post by earlycj5 on 2010-12-14
I didn't mean you had to use Darktable, I just thought that perhaps UFRAW+lensfun is only in the unstable repository that Pascal maintains for Darktable.

---

### Post by wadam on 2010-12-14
I see.  Meanwhile, alas, it looks like UFRaw has been removed from all of his PPAs.  I suppose I shall have to look elsewhere.

---

### Post by earlycj5 on 2010-12-14
> **wadam said:**
> I see.  Meanwhile, alas, it looks like UFRaw has been removed from all of his PPAs.  I suppose I shall have to look elsewhere.

So it does.

I must have a relic.

Good luck!

---

