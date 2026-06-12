---
title: "Make Firefox4 titelbarless like chrome/chromium"
date: 2011-03-01
forum: Art &amp; Design
---

### Post by arzali on 2011-03-01
Hey all,
I just wanted to show you how to make a titelbarless Firefox 4 (aka Minefield).

You need:
Minefield [http://nightly.mozilla.org/](http://nightly.mozilla.org/)
Stylish [https://addons.mozilla.org/de/firefox/addon/stylish/](https://addons.mozilla.org/de/firefox/addon/stylish/)
Hide Caption Titlebar Plus [https://addons.mozilla.org/de/firefox/addon/hide-caption-titlebar-plus-sma/](https://addons.mozilla.org/de/firefox/addon/hide-caption-titlebar-plus-sma/)
Compiz + CompizConfig setting-manager

1. Download and install Hctp and Stylish. Restart

2. Press ctrl+shift+a and open the Hide Caption Titlebar Plus Preferences

make it like in the screenshots

[[IMG]http://uppix.net/f/2/2/4813e38599a08d60af99fbff7a6det.jpg[/IMG]]("http://uppix.net/f/2/2/4813e38599a08d60af99fbff7a6de.png")
[[IMG]http://uppix.net/9/1/4/3f0631bb1216b5f219e07027f2a73t.jpg[/IMG]]("http://uppix.net/9/1/4/3f0631bb1216b5f219e07027f2a73.png")


3. right click on the tab bar and select customize.
    Now drag and drop the [hcp] Min, Max, Close Buttons next to the app menu (or anywhere you want)

[[IMG]http://uppix.net/e/7/8/9c197d14f72ecb20c970f6e98f36ct.jpg[/IMG]]("http://uppix.net/e/7/8/9c197d14f72ecb20c970f6e98f36c.png")

4. Go to [http://userstyles.org/styles/44677](http://userstyles.org/styles/44677) and install the style with stylish.

5. Open CompizConfig setting-manager (ccsm) and navigate to Decorations.
In "decoration for windows" add :   & !(class=Minefield & state=maxvert)

[[IMG]http://uppix.net/1/2/9/4cdd3bd549c6a94bac65769806ac2t.jpg[/IMG]]("http://uppix.net/1/2/9/4cdd3bd549c6a94bac65769806ac2.png")

This will remove the title bar when minefield is maximized

Now your Firefox 4 should look like this when maximized and should almost take the same space as Chrome/Chromium
[[IMG]http://uppix.net/f/a/c/fdebd6fb8de2adfe1b866e4220af0tt.jpg[/IMG]]("http://uppix.net/f/a/c/fdebd6fb8de2adfe1b866e4220af0.png")


I also made a Hctp theme for orta [http://userstyles.org/styles/44686](http://userstyles.org/styles/44686)

---

### Post by Marcelo Ruiz on 2011-03-24
Thanks for the instructions. Making Firefox look like Chrome makes me feel like using it!
I had a little problem with your instructions, and maybe you can tell me how to solve it.
I use the default gnome style for the buttons (upper right corner), and although I can drag the buttons to the right in the maximized firefox, they appear out of order (close, minimize, restore) instead of (minimize, restore, close). Is there any way to change this?
Thanks again!

---

### Post by Virus666 on 2011-04-13
That is perfect. At last I could make my **Firefox** looks like **Windows** edition.

However, installing **Stylish** and its styles just affects on the **minimize**, **maximize**, **close** buttons shape. Since it does not necessary for me, I prefer to not to install Stylish and I skiped the **fourth step**.

Moreover, we need to edit the code in the **fifth step**. The final version of Firefox 4 has released and you can install the stable PPA here:
[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

Since it is the final version, Ubuntu does not call it as **Minefield** anymore. Thus, we need to replace the Minefield part as **Firefox** in the fifth step:

```
any & !(class=Firefox & state=maxvert)
```

That's all... The screenshot is in the attachment...

Thank you... :D

---

