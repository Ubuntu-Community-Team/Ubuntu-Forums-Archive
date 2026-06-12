---
title: "Pixmap in the tray of Xfce panel"
date: 2011-11-03
forum: Art &amp; Design
---

### Post by dbbolton on 2011-11-03
I am trying to use a pixmap as the background for the xfce4-panel. It seems the system notification area or tray doesn't line up with the rest of the panel.

I made a pixmap with a single red pixel at the top and a single blue pixel at the top. Here is the screenshot: [http://i.imgur.com/BvhTx.png](http://i.imgur.com/BvhTx.png)

As you can see, the items in the notification area have an extra red stripe, suggesting that the pixmap is being applied to the items in the tray on top of, and a few pixels below, the actual panel.

I want to make the panel have a single-pixel border at the top an bottom. I'm guessing that the only way to do this would be to somehow force the tray items to have a different background image that is actually transparent. I don't know whether this is actually possible, because I think those items might be part of the same gtk class.

Even using a gradient without the border looks bad because the top 3 or so pixels have to be the same color.

The only workaround I can think of is quite sketchy: delete xfce's tray from the panel and run stalonetray or so on top of it with a transparent background. I really don't want to do that. I'm hoping a gtk wizard will know how to deal with this issue better.

EDIT: It seems the forum has (rather poorly) converted my PNG to a low-quality JPEG and you can't see the problem. Here is a direct link to the PNG file on imgur: [http://i.imgur.com/BvhTx.png](http://i.imgur.com/BvhTx.png)

---

