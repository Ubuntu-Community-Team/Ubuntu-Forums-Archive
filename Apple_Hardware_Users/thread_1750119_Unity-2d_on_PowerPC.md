---
title: "Unity-2d on PowerPC"
date: 2011-05-05
forum: Apple Hardware Users
---

### Post by pauljwells on 2011-05-05
There is a graphics bug (arguably) in Qt4 that makes the unity-2d interface colours look all wrong on PowerPC.

I have written a kludged fix for this, which is now being studied by the Devs and will no doubt be included in a future update.

If anyone wants to try my kludge it's pretty straightforward just following these instructions:

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/")

The source package is unity-2d

After the dpkg-source -x step, edit (as root) the file iconimageprovider.cpp (found in /launcher/UnityApplications)

Find the lines ```
    QImage swappedImage = image.rgbSwapped();
    g_object_unref(pixbuf);
``` near the end of the file and paste the following code between them

```
    /* Start of PJW Kludge*/
    int imageheight = swappedImage.height();
    int imagewidth = swappedImage.width();
    QRgb pixcolour;
    int pixalpha, pixred, pixgreen, pixblue;
    for (int x = 0; x < imagewidth; x++)
    {
        for (int y = 0; y < imageheight; y++)
        {
        pixcolour = swappedImage.pixel(x, y);
        pixalpha = qAlpha(pixcolour);
        pixred = qRed(pixcolour);
        pixgreen = qGreen(pixcolour);
        pixblue = qBlue(pixcolour);
        pixcolour = qRgba(pixalpha, pixblue, pixgreen, pixred);
        swappedImage.setPixel(x, y, pixcolour);
        }
    }
    /* End of PJW Kludge*/
```

Then continue with the rest of the compilation. You end up with a bunch of .deb files in the build directory that you install with

```
sudo dpkg -i ./*.deb
```

Hope this helps!

---

### Post by pauljwells on 2011-05-06
[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/758782]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/758782")

A fix will be out in unity-2d_3.10

---

### Post by teachop on 2011-05-06
Good work tracking it down.

---

### Post by pauljwells on 2011-07-16
I now regularly build the source from the unity-2d ppa if it's of any use to anyone here are the debs:

[http://db.tt/ipMLd8R]("http://db.tt/ipMLd8R")

---

