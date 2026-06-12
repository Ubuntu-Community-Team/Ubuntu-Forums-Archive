---
title: "[SOLVED] Duda sobre RAM"
date: 2007-11-15
forum: Argentina Team
---

### Post by Alejandro Vidal on 2007-11-15
Estimados,
Tengo un duda para agregar RAM a mi ubuntu 7.10 que corre sobre un P4.
Actualmente tengo dos DIMMs de 256 a 400 Mhz que están instalados en el socket 1 y 3.
La duda existencial que tengo es si puedo agregar 1 DIMM solo o si necesariamente tengo que utilizar los dos sockets restantes.
En el caso de que pueda agregar 1 es conveniente cambiar el orden o puedo dejarlos como están. Copio debajo lo que dice en el manual de mi máquina para ver si alguno me saca de la duda.
Gracias!

> Installing Additional Memory The computer comes with Double Data Rate-Synchronous Dynamic
Random Access Memory (DDR-SDRAM) Dual Inline Memory
Modules (DIMMs).
DIMMs
The memory sockets on the system board can be populated with
industry-standard DIMMs. These memory module slots are populated
with at least one preinstalled memory module. Toachieve the
maximum memory support, you may be required to replace the
preinstalled DIMM with a higher capacity DIMM.
The system board can be populated with up to 4GB of memory and
supports single-channel or dual-channel mode.
&#9998; For more information about single-channel or dual-channel memory
modes, see the section “Single and Dual Channel Modes” on page 8.
DDR-SDRAM DIMMs
For proper system operation, if the computer supports DDR-SDRAM
DIMMs, the DIMMs must be:
&#9632; industry-standard 184-pin
&#9632; unbuffered PC2100 266 MHz-, PC2700 333 MHz-, or PC3200
400 MHz-compliant
&#9632; 2.5 volt DDR-SDRAM DIMMs.
The DDR-SDRAM DIMMs must also:
&#9632; support CAS latency 2, 2.5, or 3 (CL = 2, CL = 2.5, or CL = 3)
&#9632; contain the mandatory JEDEC SPD information
In addition, the computer supports:
&#9632; 128Mbit, 256Mbit, and 512Mbit non-ECC memory technologies
&#9632; single-sided and double-sided DIMMS
&#9632; DIMMs constructed with x8 and x16 DDR devices; DIMMs
constructed with x4 SDRAM are not supported
1–8 Hardware Reference Guide
Hardware Upgrades
Maximum operating speed is determined by a combination of the
CPU and type of memory used. Refer to the table below for the
optimum combination.
&#9998; The system will not start if you install unsupported DIMMs.
Single and Dual Channel Modes
HP Compaq dx2000 Microtower models will automatically operate in
single channel mode or a higher-performing dual channel mode,
depending on how the DIMMs are installed.
&#9632; In single channel mode, the maximum operational speed is
determined by the slowest DIMM in the system. For example, if
the system is populated with a DIMM that is 266 MHz and a
second DIMM that is 333 MHz, the system will run at the slower
of the two speeds.
&#9632; In dual channel mode, all DIMMs must be identically matched.
DIMMs in the J23 and J24 sockets must be identical; DIMMs in
the J25 and J28 sockets must also be identical. Therefore, if you
have one preinstalled DIMM in socket J23 and are adding a
second DIMM, it is recommended that you install an identical
DIMM into the J25 socket. If you are populating all four DIMM
sockets, use identical DIMMs in each socket. Otherwise, the
system will not operate in dual channel mode.
Maximum Front Side Bus Operating Speed (MHz)
CPU Front Side Bus
(MHz)
DDR266 DIMM
DDR333 DIMM
DDR400
DIMM
400266266266
533266333333
800266320400
Hardware Reference Guide 1–9
Hardware Upgrades
There are four DIMM sockets on the HP Compaq dx2000 Microtower
system board, operating in either single- or dual-channel mode, with
two sockets per channel. The sockets are labeled J23, J24, J25, and
J28. Sockets J23 and J24 operate in memory channel A. Sockets J25
and J28 operate in memory channel B.

---

### Post by fscodelaro on 2007-11-15
Tengo entendido que se puede agregar uno solo (a los dos existentes). Si uno agrega los dos a la vez, funciona más rápido (Dual channel). Yo tengo 1 de 4 ocupado asi que supongo que 3 de 4 será igual. No necesitás cambiar la disposición de los que ya están, simplemente agregá el tercero en el slot que está más cerca del micro.

Al pasar a ser single channel speed, la velocidad máxima va a ser la de la memoria más lenta (que puede que sea menos de 400 Mhz). Pero de todas maneras yo preferiría más RAM aunque sea un poco más lenta, sobre todo en el nivel de 512 mb.

---

### Post by Alejandro Vidal on 2007-11-15
Gracias por la respuesta.
Mi última duda es si afecta en algo si ahora agrego un DIMM de 512 cuándo tengo instalados dos de 256. Voy a comprar uno de 400 MHz por lo que los tres van a ser de 400MHz y voy a llegar la RAM a 1giga reservando un socket libre por si en algún momento se me hace necesario agregar más RAM.
Siempre soy así de indeciso antes de largar un mango ;)

---

### Post by niko_3100 on 2007-11-15
Si vas a largar un mango ponele un gb mas no 512, para mi va a ser mejor.

---

### Post by margori on 2007-11-15
Estimado Alejandro:

Segun lo que copiaste del manual, habla sobre junper J23, J24,J25 y J28, y no sobre slot 1,2,3 y 4. Voy a suponer que J23 = Slot1, J24 = Slot2, J25 = Slot3 y J28 = Slot4.

Si esto es asi, en tu configuración actual, slots 1 y 3, no estas aprovechando el dual-channel debido a que, para usarlo, deben haber 2 ddr identicas en los slots 1 y 2. Asi que si agregas un DDR adicional no cambiaria la situación, seguirias sin usar el dual-channel.

Lo que haria en tu situacion es mover el DDR del slot 3 al 2 y ver si se habilita el dual channel. Si es asi, lo dejas en el 2 y pones un DDR nuevo en el 3. Sino da igual lo que hagas, no podras usar dual channel porque tendrias 3 DDR diferentes.

Lo mejor que podes hacer para tener 1GB es vender los 2 DDR de 256MB que tenes ahora y comprar 2 ddr de 512MB identicos. Se que no es la misma plata, pero harias el mejor uso de las capacidades de tu placa madre.

---

### Post by Alejandro Vidal on 2007-11-15
> **margori said:**
> 
Lo que haria en tu situacion es mover el DDR del slot 3 al 2 y ver si se habilita el dual channel. Si es asi, lo dejas en el 2 y pones un DDR nuevo en el 3. Sino da igual lo que hagas, no podras usar dual channel porque tendrias 3 DDR diferentes.

Lo mejor que podes hacer para tener 1GB es vender los 2 DDR de 256MB que tenes ahora y comprar 2 ddr de 512MB identicos. Se que no es la misma plata, pero harias el mejor uso de las capacidades de tu placa madre.

Lo primero que voy a hacer es mover el DIMM que tengo al 2 para ver si se habilita el dual channel. 
Un par de preguntas más:
1 - ¿Cuándo se habla de DIMMs idénticos se hace referencia solo a la cantidad de MHz o también al tamaño?
2 - ¿Cuál es la ventaja de habilitar el dual channel? Por lo que entendí es solo evitar que iguale los (MHz) hacia abajo. En mi caso va a ser todo a 400Mhz. ¿En ese caso da igual o el dual channel presenta alguna otra ventaja?
Gracias nuevamente!

---

### Post by margori on 2007-11-15
Cuando hablo de DDR identicos no solo son MHz y tamaño. Se que hay mas cosas, pero como no soy especialista en eso, la verdad no lo se.

Cual es la ventaja de Dual Channel? Al utilizar dos canales de comunicacion, se aumenta la tasa de transferencia desde la RAM al Microproc. Normalmente no se duplica la tasa sino que llega a un 80% mas de velocidad que la tasa original. Es decir que con dos ddr de 256MB de 400MHz usando dual-channel, tendrias un rendimiento comparable a 1 DDR de 512MB de 720MHz. Asi que tu veras las ventajas del dual-channel.

Te pido no te quedes solo con lo que yo te digo. No soy para nada especialista. Esto lo he aprendido de hobby. Soy ingeniero industrial.

---

### Post by Alejandro Vidal on 2007-11-15
Gracias por la data.
En wikipedia encontré lo siguiente:
[http://en.wikipedia.org/wiki/Dual-channel_architecture]("http://en.wikipedia.org/wiki/Dual-channel_architecture")
Por lo que dice no existe gran diferencia. De todas formas voy a probar y después les cuento.
> Actual results

Tom's Hardware found no significant difference between single-channel and dual-channel configurations in synthetic and game benchmarks.[2] Generally speaking, dual channel configuration is a very minor upgrade, and without other system tweaks, the difference may not even be noticeable. While there is no reason not to use dual-channel over single-channel, where all other things are equal, the question often comes up whether it is advisable to add additional RAM if doing so will break dual-channel compatibility. Having more total RAM available is generally more beneficial than maintaining dual-channel configuration.

Saludos.

---

### Post by Alejandro Vidal on 2007-11-15
Aporto otro informe interesante:
[http://www.kingston.com/newtech/MKF_520DDRwhitepaper.pdf]("http://www.kingston.com/newtech/MKF_520DDRwhitepaper.pdf")
En la página 9 tiene un gráfico super ilustrativo.
Lo primero que voy a hacer es ver de que modo puedo averiguar si los dos DIMMs que actualmente tengo son idénticos y luego verificar que actualmente esten trabajando en dual channel mode. ¿alguno sabe cómo puede verificarse?
Luego en función de eso voy a definir si me conviene conseguir otros dos idénticos para quedar en un giga aprovechando el dual channel mode o agregar más ram y olvidarme de los beneficios del dual channel.
Otra buena es la que me sugirieron de comprar dos iguales de 512 y vender o regalar las de 256 :)
Saludos.

---

### Post by Alejandro Vidal on 2007-11-15
Ya en mi casa comencé a investigar como podía verificar si los DIMMs que tengo instalados en Dual Channel Mode.
Recordé el viejo y conocido F10 y me encontré con lo siguiente bajo memory information:
> DDR FREQUENCY: 333MHz Dual Channel Mode
Memory DIMM1: 256MB
Memory DIMM2: Not Installed
Memory DIMM3: 256MB
Memory DIMM4: Not Installed
Available System Memory: 504MB
Legacy VGA Memory: 8MB

Mis conclusiones son dos:
La primera que los chantas que me vendieron la máquina me dijeron que los DIMMs eran de 400MHz pero en realidad eran de 333MHz.
La segunda que estan bien instalados para activar el Dual Channel Mode.

Creo que voy a comprar dos de 512 a 400MHz para reemplazar los actuales y punto. :-k

---

