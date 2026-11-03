# Facts ledger — ADC 验证及测试培训课件

Source key: `doc` = adc验证及测试.docx；`calc` = 由表中条目计算；`ref` = 网络来源(见 URL 列)。

| fact | value | unit | source |
|---|---|---|---|
| 转换关系 | DOUT = 2^n·G·AIN/VREF | - | doc §概述 |
| 例: 3bit, VREF=8V, VIN=5.5V | 输出 101 | - | doc §分辨率 |
| LSB | VREF/2^n | V | doc/doc标准 |
| 例: 3.3V, 12bit | 0.806 | mV | calc |
| 奈奎斯特 | fs ≥ 2·fm | Hz | doc §采样 |
| 采样保持建立 | ts ≥ (n+1)·ln2·RC | τ | ref(标准) |
| 例: 12/16/20 bit | 9.0 / 11.8 / 14.5 | τ | calc |
| 量化噪声方差 | σ² = Δ²/12 | - | doc §量化误差 |
| 理想 SNR | 6.02N + 1.76 | dB | doc + ref(Analog MT-001) |
| 例: N=12/14/16/18/20 | 74.0 / 86.0 / 98.1 / 110.2 / 122.2 | dB | calc |
| 每加 1 bit | +6.02 | dB | calc |
| ENOB | (SINAD − 1.76)/6.02 | bit | doc |
| 例: SINAD=71.5dB | 11.6 | bit | calc |
| 抖动 SNR | −20·log10(2π·f·σt) | dB | ref(AD AN-756) |
| 例: σt=1ps, f=10kHz/1MHz/100MHz | 144.0 / 104.0 / 64.0 | dB | calc |
| SFDR 经验 | ≈ SNR + 10 | dB | doc §动态 |
| SINAD 判差 | 理论值 − 6dB 视为较差 | dB | doc §动态测试 |
| DNL | (W[k]max − VLSB)/VLSB | LSB | doc §标准DNL |
| 丢码 | DNL ≤ −1.0 | LSB | doc |
| INL | ΔVmax/VLSB | LSB | doc §标准INL |
| OFFSET(单极) | EO = T[1] − 0.5·VLSB | V | doc §标准OFFSET |
| OFFSET(双极) | EO = T[2^N−1] − (−0.5·VLSB) | V | doc §标准OFFSET |
| GAIN | EG = {[(T[2^N−1]−T[1])/(VFSR−2·VLSB)] − 1}×100 | %FSR | doc §标准GAIN |
| 两点法 12bit | V1=0.25·Vref, V2=0.75·Vref | - | doc §OFFSET/GAIN测试 |
| 直方图采样量 | α=0.05, Z=2.58, β=0.1, 公式见图 | - | doc §DNL/INL |
| 相干采样 | Nsample/Fsample = M/Fsignal, gcd(M,N)=1 | - | doc + ref(TI SLVAG04) |
| FFT 点数 | 16384 | 点 | doc §动态 |
| 频箱宽度 | Δf = fs/N | Hz | doc/ref |
| 中断输出速率 | < 1Msps | SPS | doc §机测 |
| DMA 速率 | ≥ 1Msps | SPS | doc §机测 |
| DMA 计时采样数 | 32768 | 点 | doc §机测 |
| 通道扫描点数(芯片验证) | 0,5,50,100mV, 1/8,1/4,3/8,1/2,5/8,3/4,1×Vref, Vref+0.1V | - | doc §通道扫描 |
| 覆盖段数 | ≥ 8 | 段 | doc §通道扫描 |
| 判据(芯片验证) | ±20 | mV | doc §通道扫描 |
| 判据(机测) | ±100 | mV | doc §机测通道扫描 |
| 连续转换测试点 | 1/4, 1/2, 1×Vref, 差值<10 | mV | doc §连续转换 |
| 采样时间判据 | Freq = 1/(Ts+Tv)×2 | - | doc §采样时间 |
| 通道间一致性 | 每通道16次平均, ±5 | LSB | doc §通道电压对比 |
| 温度传感器 | 25–120℃, 8 点 | ℃ | doc §温度传感器 |
| VREFMin 规则 | ≥2.4V: VREFMin/2.5or3V/AVcc; ≥1.4V: +1.5V | - | doc §参考电压 |
| 老化测试电压 | 1/2·Vref | - | doc §老化 |
| 校准 | 12bit 仅 OFFSET; 16bit OFFSET+INL; 基准 ≤0.001V | - | doc §校准 |
| 同步一致性 | ΔENOB ≤ 0.5 | bit | doc §同步 |
| 异步劣化 | ΔENOB ≤ 1 | bit | doc §异步 |
| CMRR | 20·lg(VIN/VOUT) | dB | doc §CMRR |
| PSRR | (M2−M1)/(ΔVPS/VPS) | - | doc §PSRR |
| 去耦电容 | <5mm, 10uF钽 + 0.1uF 0603 + 1nF 0402 | - | doc §ATE板 |
| REF 走线 | <10mm, ≥20mil, 地线包裹 | - | doc §ATE板 |
| 模拟走线间距 | ≥ 3×线宽 | - | doc §ATE板 |
| 时钟/触发 GPIO | 50Ω 阻抗控制 | - | doc §ATE板 |
| 评估板存储 | SDRAM 1MB–16MB | - | doc §评估板 |
| 评估板晶振 | 0.1% 无源 | - | doc §评估板 |
| 17 项验证清单 | 复位/寄存器/通道/Vref/连续/触发/时钟/分频/时间/DMA/中断/温度/通道对比/静态/动态/校准 | - | doc 表1 |

URL:
- https://www.analog.com/media/en/training-seminars/tutorials/MT-001.pdf
- https://www.analog.com/en/resources/technical-articles/coherent-sampling-vs-window-sampling.html
- https://www.ti.com/lit/an/slvag04
- https://www.analog.com/media/en/technical-documentation/application-notes/AN-756.pdf
- https://www.analog.com/en/resources/technical-articles/histogram-testing-determines-dnl-and-inl-errors.html
- https://www.ti.com/lit/an/sbaa002a
