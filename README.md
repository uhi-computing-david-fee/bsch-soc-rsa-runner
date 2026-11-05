# RSA Investigator

A browser-based tool for investigating RSA key behaviour in the Science of Computing & Digital Media unit. Enter small prime values and public and private exponents, then test selected messages or the complete permitted message range. The application reports encryption, decryption, message recovery and ciphertext collisions. The focus is on experimental evidence and analysis; students do not need to write code.

## Run the application

The application is a single HTML file. Open `rsa-investigator.html` in a modern browser. It runs locally and does not require installation, a server or an internet connection.

No separate data directory or other files are required.

## Configure an experiment

Enter two distinct prime numbers for `p` and `q), and positive whole numbers for the public exponent `e` and private exponent `d`. The application calculates:

- `n = p × q`
- `φ(n) = (p − 1) × (q − 1)`

The default values (`p = 5`, `q = 11`, `e = 3`, `d = 27`) provide a small working example. Students should construct and explain their own keys for their investigation.

The application deliberately allows positive exponent values that do not satisfy the usual key-generation relationship. This lets students examine their behaviour. It does not calculate `e` or `d) for them.

The modulus is limited to 10,000 so that a complete message-range test remains practical. The primes must be distinct. Prime checking uses trial division, which is suitable for these small teaching inputs, not for cryptographic key generation.

## Choose messages

Select one of two test modes:

- **Selected messages** — enter non-negative whole numbers separated by commas, spaces or new lines. Each message must be in the permitted range, from `0` to `n − 1`, and can only appear once in the list.
- **Every permitted message** — tests the complete range from `0` through `n − 1`.

For each message `m`, the application calculates ciphertext `c = m^e mod n), then calculates the recovered value `c^d mod n`. It records whether the recovered value matches the original message.

## Results and export

The results show the key values, number of messages tested, number and percentage recovered correctly, and number of distinct ciphertexts among the tested messages. The collision section lists up to ten examples where different tested messages produced the same ciphertext.

Message results are displayed in pages of up to 100 rows. Select **Download all results as CSV** to save every row, including results not currently shown on screen. The CSV includes the experiment label, run identifier, date and time, key values, original message, ciphertext, recovered message and match result.

Results are held in the browser only while the page remains open. Download the CSV before starting another experiment if you need to keep a record; each new run replaces the previous results in the page.

## Notes for interpreting results

A complete-range test establishes the behaviour of the entered key values for that modulus. It does not establish behaviour for every possible RSA key. A successful recovery test also does not establish that small textbook RSA values are secure for practical use.

A ciphertext collision means that two distinct tested messages produced the same ciphertext. Interpret collisions alongside the messages and key values tested. The application reports observations; it does not decide whether an RSA claim is supported.

The application accepts only permitted messages, from `0` to `n − 1`. Messages outside this range are rejected.
