# VByte

Pure-rust implementation of VByte algorithm

This is a fork of [perlin-core](https://github.com/CurrySoftware/perlin-core/tree/d60c665192e865c8f3e68f6ca28c6cfe361c0351)

## Usage

```rust
// Encode
let mut buffer = vec![];
let len = vbyte_encode(vec![0, 130, 5, 65535, 0, 6, 2, 5, 4, 131].as_slice(), &mut buffer);
assert_eq!(buffer, vec![0x80, 0x01, 0x82, 0x85, 0x03, 0x7F, 0xFF, 0x80, 0x86, 0x82, 0x85, 0x84, 0x01, 0x83]);

// Decode
let decoder = VByteDecoder::new(buffer.as_slice());
assert_eq!(decoder.collect::<Vec<_>>(),
            vec![0, 130, 5, 65535, 0, 6, 2, 5, 4, 131]);
```

## License

MIT