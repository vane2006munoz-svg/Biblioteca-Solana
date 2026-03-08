const solana = require("@solana/web3.js");
const splToken = require("@solana/spl-token");

// Conectar a la red de prueba
const connection = new solana.Connection(
  solana.clusterApiUrl("devnet"),
  "confirmed"
);

// Crear wallet
const payer = solana.Keypair.generate();

async function crearToken() {

  // Crear token
  const token = await splToken.createMint(
    connection,
    payer,
    payer.publicKey,
    null,
    9
  );

  console.log("Token creado:", token.toString());
}

crearToken();
