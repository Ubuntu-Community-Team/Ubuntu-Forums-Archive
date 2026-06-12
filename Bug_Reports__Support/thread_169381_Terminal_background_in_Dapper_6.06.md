---
title: "Terminal background in Dapper 6.06"
date: 2006-05-02
forum: Bug Reports / Support
---

### Post by bluez34me on 2006-05-02
I'm running into a funny issue with the background in Terminal on Dapper. I have set a background image (tux) which displays fine when the terminal is first opened, but which has display problems if I move or resize the window.

It appears that this problem is related to the fact that the image has a transparent background. If it is either a gif or png with transparency, I get a lot of garbage on the screen (distorted colors, reversed colors, other screen sections) when moving or resizing the window containing terminal. If I save it without a transparent background (or as a jpg) then everything's cool.

I'm not sure if this is a problem with x, a problem with the terminal, or what. But it's definitely a bug.

---

