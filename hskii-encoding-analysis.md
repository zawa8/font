# hskii Encoding System Analysis

## Overview

hskii is a phonetic encoding system that maps 38 human speech sounds to 
single-case characters, integrates 6 dedicated hex digits, and reserves 8 
uppercase letters for programming symbols. Total usable characters: 128 
(ASCII range).

## Phonetic Mapping

### Base Sounds (26 lowercase)

| hskii | Hindi | Example |
|-------|-------|---------|
| a | अ | a = अ |
| b | ब | ba = ब |
| c | च | ca = च |
| d | ड | da = ड |
| e | ए | e = ए |
| f | फ | fa = फ |
| g | ग | ga = ग |
| h | ह | ha = ह |
| i | इ | i = इ |
| j | त | ja = त |
| k | क | ka = क |
| l | ल | la = ल |
| m | म | ma = म |
| n | न | na = न |
| o | ओ | o = ओ |
| p | प | pa = प |
| q | द | qa = द |
| r | र | ra = र |
| s | स | sa = स |
| t | ट | ta = ट |
| u | उ | u = उ |
| v | ह | va = हा |
| w | व | wa = वा |
| x | ə | x = schwa |
| y | य | ya = य |
| z | ज | za = ज |

### Aspirated/Modified Sounds (12 capitals)

| hskii | Hindi | Sound |
|-------|-------|-------|
| K | ख | aspirated k |
| G | घ | aspirated g |
| C | छ | aspirated c |
| Z | झ | aspirated z |
| T | ठ | aspirated t |
| D | ढ | aspirated d |
| J | थ | aspirated j |
| Q | ध | aspirated q |
| B | भ | aspirated b |
| S | श | aspirated s |
| N | ं | nasal |
| R | ड़ | retroflex r |

## Dedicated Hex Digits (6 capitals)

| hskii | Value | Mnemonic |
|-------|-------|----------|
| L | 10 | ten (8+2) |
| Y | 11 | yilewen (8+3) |
| V | 12 | twelw (8+4) |
| W | 13 | dblun (8+5) |
| P | 14 | purxn (8+6) |
| F | 15 | fiwxn (8+7) |

### Key Equation
8+8 = 10 = 4×4 = F+1 = P+2 = W+3 = V+4 = Y+5 = L+6


### Why these letters?

| Letter | Phonetic Status | Reason |
|--------|-----------------|--------|
| L | same as l | No different sound, free to use |
| Y | same as y | No different sound |
| V | same as v | No different sound |
| W | same as w | No different sound |
| P | same as p | No different sound |
| F | same as f | No different sound |

### Why NOT these?

| Letter | Phonetic Status |
|--------|-----------------|
| K | different from k (ख vs क) |
| G | different from g (घ vs ग) |
| C | different from c (छ vs च) |
| Z | different from z (झ vs ज) |
| T | different from t (ठ vs ट) |
| D | different from d (ढ vs ड) |
| J | different from j (थ vs त) |
| Q | different from q (ध vs द) |
| B | different from b (भ vs ब) |
| S | different from s (श vs स) |
| N | different from n (nasal) |
| R | different from r (ड़ vs र) |

## Programming Symbols (8 capitals)

| hskii | Symbol | Meaning |
|-------|--------|---------|
| E | `==` | is-equal-to |
| U | `!=` | not-equal-to |
| I | `>=` | greater-than-or-equal-to |
| O | `<=` | less-than-or-equal-to |
| M | `&&` | logical AND |
| X | `\|\|` | logical OR |
| A | `=>` | arrow/lambda |
| H | `++` | increment |

### Why these letters?

| Letter | Symbol | Reason |
|--------|--------|--------|
| E | `==` | E for Equal |
| U | `!=` | U for Unequal |
| I | `>=` | I resembles ≥ |
| O | `<=` | O resembles ≤ |
| M | `&&` | M for Multiple conditions |
| X | `\|\|` | X for eXclusive OR |
| A | `=>` | A for Arrow |
| H | `++` | H for High increment |

## Complete Character Set

### Total: 44 defined characters

| Category | Count | Characters |
|----------|-------|------------|
| Digits | 10 | 0-9 |
| Base sounds | 26 | a-z |
| Aspirated | 12 | K,G,C,Z,T,D,J,Q,B,S,N,R |
| Hex digits | 6 | L,Y,V,W,P,F |
| Programming | 8 | A,E,I,O,U,M,X,H |

### Remaining: 84 slots (of 128) available

## hskii vs ASCII vs Unicode

### Comparison Table

| Feature | ASCII | Unicode | hskii |
|---------|-------|---------|-------|
| Char size | 1 byte | 1-4 bytes | 1 byte |
| Universal sounds | ❌ | ❌ | ✅ |
| Phonetic typing | ❌ | ❌ | ✅ |
| Simple rendering | ✅ | ❌ | ✅ |
| Native hex | ❌ | ❌ | ✅ |
| Standard keyboard | ✅ | ❌ | ✅ |
| Cross-language | ❌ | Partial | ✅ |
| Case sensitivity | 2 cases | varies | 1 case |
| Programming symbols | ✅ | ✅ | ✅ (8 reserved) |

### Storage Efficiency

| Text | ASCII/UTF-8 | hskii | Savings |
|------|-------------|-------|---------|
| हाथी | 12 bytes (UTF-8) | 4 bytes | 3× |
| वकील | 12 bytes (UTF-8) | 5 bytes | 2.4× |

## Number System: plong

### Format
-2P,5V,67,5V.67.78.89


- Comma separates integer digits
- Period separates fractional digits
- Each digit = one u8 (0-255, displayed as hex pair)
- Base-256 storage

### Example
cplong x("-2P,5V,67,5V.67.78.89");
// wlyu = [46, 92, 103, 92, 103, 120, 137]
// start_prisizxn_leyr = 3
// is_negetiw = true


## Advantages of hskii

1. **Universal phonetic representation** - one sound = one symbol
2. **Compact storage** - 1 byte per sound
3. **Simple rendering** - no complex text layout
4. **Native hex support** - L,Y,V,W,P,F
5. **QWERTY-compatible** - no special keyboard
6. **Cross-script** - works for Hindi, Urdu, Bengali, etc.
7. **Easy to parse** - fixed width, no ambiguity
8. **Programming-ready** - 8 symbols for operators

## Disadvantages

1. **Limited to 44 defined characters**
2. **Learning curve** - phonetic mapping
3. **Not standard** - no existing infrastructure
4. **Glyph ambiguity** - v may look like H
5. **Single case** - no upper/lower distinction

## Verdict

hskii is superior for:
- Phonetic keyboard input
- Cross-language text storage
- Arbitrary-precision numbers
- Compact text representation

Not suitable for:
- Standard text documents (compatibility)
- Mathematical notation
- Emojis/symbols

## References

- Font: https://github.com/zawa8/font/tree/main/ttf/hscii
- Keyboard: https://github.com/zawa8/xNglobord
- Number system: https://github.com/zawa8/plong
