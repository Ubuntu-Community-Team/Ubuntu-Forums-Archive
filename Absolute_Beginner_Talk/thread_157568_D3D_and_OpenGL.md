---
title: "D3D and OpenGL"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-09
is there anyway to make the sure that D2D and OpenGL is working

---

### Post by nanotube on 2006-04-09
[QUOTE=slipk487]is there anyway to make the sure that D2D and OpenGL is working[/QUOTE]

in a terminal, type command "glxinfo", and see if the output contains the line "direct rendering: Yes". if it does, then your opengl is working.
d3d is a strictly-microsoft technology, so it is not present on linux, afaik.

---

### Post by Kurt` on 2006-04-09
You can also try:

glxdemo

glxgears

glxheads

heads will dump something like this:
> kurt@spark:~$ glxheads
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x805e340
  Window:      0x3000002
  Context:     0x8096780
  GL_VERSION:  2.0.0 NVIDIA 76.67
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce FX 5600/AGP/SSE/3DNOW!
If you don't see the correct video card there, there might be a problem ;)

On every other distro I've tried, glxgears dumps how many times the window was redrawn to stdout (the console most likely), but it doesn't on ubuntu.

---

