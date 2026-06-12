---
title: "Configurar el antialiasing y el anisotropic filtering para el escritorio en Placas Nv"
date: 2007-12-21
forum: Argentina Team
---

### Post by oldbluekid on 2007-12-21
Configurar el antialiasing y el anisotropic filtering para el escritorio en Placas Nvidia en Ubuntu 7.10.

Elijan uno de estos modos de antialiasing (según su placa de video) y ponganlo en el archivo "/etc/environment" así, "sudo gedit /etc/environment", por ejemplo: __GL_FSAA_MODE="4", luego reinicien X, cierren sesion, o reinicien ubuntu.


__GL_FSAA_MODE 	GeForce4 MX, GeForce4 4xx Go, Quadro4 380,550,580 XGL, and Quadro4 NVS
0 	FSAA disabled
1 	2x Bilinear Multisampling
2 	2x Quincunx Multisampling
3 	FSAA disabled
4 	2 x 2 Supersampling
5 	FSAA disabled
6 	FSAA disabled
7 	FSAA disabled

__GL_FSAA_MODE 	GeForce3, Quadro DCC, GeForce4 Ti, GeForce4 4200 Go, and Quadro4 700,750,780,900,980 XGL
0 	FSAA disabled
1 	2x Bilinear Multisampling
2 	2x Quincunx Multisampling
3 	FSAA disabled
4 	4x Bilinear Multisampling
5 	4x Gaussian Multisampling
6 	2x Bilinear Multisampling by 4x Supersampling
7 	FSAA disabled

__GL_FSAA_MODE 	GeForce FX, GeForce 6xxx, GeForce 7xxx, Quadro FX
0 	FSAA disabled
1 	2x Bilinear Multisampling
2 	2x Quincunx Multisampling
3 	FSAA disabled
4 	4x Bilinear Multisampling
5 	4x Gaussian Multisampling
6 	2x Bilinear Multisampling by 4x Supersampling
7 	4x Bilinear Multisampling by 4x Supersampling
8 	4x Bilinear Multisampling by 2x Supersampling (available on GeForce FX and later GPUs; not available on Quadro GPUs)

__GL_FSAA_MODE 	GeForce 8xxx, G8xGL
0 	FSAA disabled
1 	2x Bilinear Multisampling
2 	FSAA disabled
3 	FSAA disabled
4 	4x Bilinear Multisampling
5 	FSAA disabled
6 	FSAA disabled
7 	4x Bilinear Multisampling by 4x Supersampling
8 	FSAA disabled
9 	8x Bilinear Multisampling
10 	8x
11 	16x
12 	16xQ
13 	8x Bilinear Multisampling by 4x Supersampling

Si les interesa también pueden agregar en el mismo archivo una variable para configurar el filtro anisotrópico:

__GL_LOG_MAX_ANISO 	Filtering Type
0 	No anisotropic filtering
1 	2x anisotropic filtering
2 	4x anisotropic filtering
3 	8x anisotropic filtering
4 	16x anisotropic filtering

Por ejemplo: __GL_LOG_MAX_ANISO="4"

---

