# 2-stage-Differential-Operational-Amplifier

# Objectives:
I have designed a Two Stage CMOS operational amplifier which operates at 1.8V power supply using the BSIM device models of a representative 180nm CMOS technology. The OPAMP designed is a two-stage CMOS OPAMP to exhibit a unity gain frequency of 30MHz and exhibits a gain of 60dB. Simulation results are verified using Cadence.

# Design Specifications:
+ Open loop gain = 10^3 = 60dB
+ Bandwidth = 30 MHz
+ Power Voltage Supply (Vdd) = 1.8 V
+ Slew Rate (V/μs) = 20 V/ μs
+ ICMR(+)=1.6 V, ICMR(-)=0.8 V
+ Load capacitance = 2 pF
+ Phase margin >= 60°
+ Power <= 8 mW

  # Desgin Description:
 + To achieve high gain systems we require two stage op amps as their amplifications get compounded.
+ The first stage is a differential pair with active load, followed by the second NMOS load.
+ The introduction of two stages causes two capacitances, at load of both stages making it a two pole system.
+ Two avoid instability and reduce oscillations due to poor phase margins an additional miller capacitance is used to  transform the system into effectively an one pole system (by dominant pole shift)
+ A reference current is mirrored across the circuit so as to bias currents source loads.

  # Design Calculations:
   ### 1. Assumptions and Values used-
       (1) Single ended output is taken

     (2) M1 and M2 are identical

     (3) M3 and M4 are identical

     (4) Higher current flows in outer circuit to provide high swing, than in the inner circuit

     (5) µpCox = 65 µA/V^2 and µnCox = 300 µA/V^2

     (6) Vthp = -0.42 V and Vthn = 0.4 V

     (7) Lmin=180nm but we are using L=500nm for lamda to be very small.

 ### 2. Calculation of miller capacitance C1 –
   C1>=  0.22  C2 (for the phase margin of 60°)

  C1>=440 fF  For calculations we are using 800 fF

  ### 3. Calculation of current through M5 (I5 )–
    I5 >= slew rate x  C1

  I5 >= 16 uA

  So we are using I5 = 20 uA
  ### 4. Calculation of (W/L)1,2 –

    gm(1,2) = Gain bandwidth x C1 x 2π

  gm(1,2) = 160 uA/V


 (W/L)1,2 = g^2m(1,2) / UnCox I5

  (W/L)1,2 = 5 

  ### 5. Calculation of (W/L)3 –
   (W/L)3,4) 	= 2 I3 / UpCox[Vdd-ICMR(+) - |Vtp|+Vtn]

 (W/L)3,4 = 14 

 ### 6. Calculation of VDsat of M5 MOSFET-
  VDsat >= ICMR(-) – (I5 / UnCox (W/L)1)^1/2 - Vtn

 VDsat >=10 mV

 So we are taking VDsat =100 mV bcz to design M5 with VDsat = 10 mV we are required very large MOSFET.

 ### 7. Calculation of (W/L)5,6 –

 (W/L)5,6 = 2 I5 / Un Cox (VDsat)^2

(W/L)5,6 = 12

### 8. Calculation of (W/L)7 –
     For the phase margin to be 60° gm,6 >=10 gm,1

     gm,6 >= 1600 uA/V

     VDS,7 = VDS,4 (Approximately)

     Vgs,7 = Vgs,4 (Approximately)

     (W/L)7 / (W/L)4 = gm,7 / gm,4

     gm,4 =( UpCox(W/L)4)^1/2

     (W/L)7 = 172

  ### 9. Calculation of (W/L)8 –
(W/L)7 / (W/L)4 = I7 / I4
 I7 = I8 = 125 uA
 Vgs,8 = Vgs,6
 (W/L)8 / (W/L)6 = I8 / I6
  (W/L)8 = 75

  ### 10. Theoretical values of W and L for All the MOSFET-
  
      MOSFET	               W	                 L
      M1,2	             2.5 um	             500nm
      M3,4	              7 um	             500nm
      M5,6	              6 um	             500nm
       M7	               86 um	             500nm
       M8	              37.5 um	             500nm

### 11. Practical values of (W/L) ratio for MOSFET-

    MOSFET	                W	                 L
      M1,2	             3.5 um	             500nm
      M3,4	             7.2 um	             500nm
      M5,6	              6 um	             500nm
       M7	               86 um	             500nm
       M8	               38 um	             500nm
## 12. Simulation Results:

  (1) Gain – Vin,1-Vin,2 = Vid = 198.4 uV

Vout= 198.2 mV

Gain = Vout/Vid = 998.99 (Approximately 1000 as per our requirement)

Gain (In DB) = 20 Log10(998.99)=59.9 DB (Approximately 60 DB as per our requirement)

(2) Gain bandwidth –

Gain bandwidth = 31.54 MHz (Fulfilling our requirement)

(3) Phase margin –

Phase margin = 61.56° (Fulfilling our requirement)
  
  
