---
title: "flv converter"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-11-13
anyone know any flv converters for linux

---

### Post by tychocity on 2006-11-13
ffmpeg -i movie.mov movie.flv

bye

---

### Post by juantovarm on 2006-11-14
Go to synaptic, add ffmpeg

When converting a flv movie to another format:

go to the terminal, go to the folder where the flv is located

ffmpeg -i movie.flv movie.avi (if it's avi what you want if you want another format, just change the extension)



Juan

---

### Post by jonathan21 on 2006-11-14
thanks will try

---

### Post by mtron on 2006-11-14
try this howto i wrote some time ago for dapper. it should work for edgy too, but don't use my provided ffmpeg package for dapper! 

[http://www.ubuntuforums.org/showthread.php?t=280652](http://www.ubuntuforums.org/showthread.php?t=280652)

---

